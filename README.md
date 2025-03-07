# Project: SOAR EDR Automation for Threat Detection and Response

This project implements an automated Security Orchestration, Automation, and Response (SOAR) solution to detect and respond to threats in real-time. By integrating LimaCharlie for endpoint telemetry, Tines for automation, and Slack for alerting, the system automates the process of detecting suspicious activity and isolating compromised systems. The goal is to enhance the incident response workflow and reduce manual intervention by automating threat detection, alerting, and remediation actions.

## Key Features

- **LimaCharlie**: Provides endpoint telemetry for real-time detection of suspicious activity. Telemetry from LimaCharlie is used to trigger detection rules and automated responses based on events such as LaZagne tool usage.
- **Tines**: Orchestrates the automated workflow by handling detection alerts, sending notifications through Slack and email, and prompting the user to isolate compromised systems. Tines ensures the incident response process is smooth and efficient.
- **Slack**: Sends real-time alerts to security personnel with detailed information about the detected threat, including process details, file paths, and command-line arguments, enabling swift action.
- **Automated Isolation**: Triggers machine isolation through an automated workflow based on user input. If a machine is compromised, it will be automatically isolated to prevent further damage.

## Technologies Used:
- **LimaCharlie**: For endpoint detection and telemetry collection.
- **Tines**: For automating and orchestrating security workflows and responses.
- **Slack**: For real-time alerts and communications.
- **Webhooks**: For automating actions and integrating tools into a cohesive workflow.

## Project Walk-through

### 1. Project Overview Diagram
This diagram illustrates the entire end-to-end workflow of the SOAR EDR playbook, showcasing how LimaCharlie, Tines, and Slack work together to automate detection and response.

![Project Overview Diagram](https://github.com/sufani/SOAR-EDR-Automation-for-Threat-Detection-and-Response/blob/main/images/SOAR%20EDR%20Project.drawio.png?raw=true)

### 2. Deploying Servers on Vultr
This screenshot shows the Vultr servers used in the project, including the **MySOAR-EDR server** deployed to handle LimaCharlie and other components for event detection and incident response.

![Vultr Server Deployment](https://github.com/sufani/SOAR-EDR-Automation-for-Threat-Detection-and-Response/blob/main/images/VultrServer.jpeg?raw=true)

### 3. Installing and Configuring LimaCharlie
#### LimaCharlie Configuration
I configured LimaCharlie to collect telemetry data from endpoints. This step included setting up LimaCharlie on the server to monitor system activities.

![LimaCharlie GUI](https://github.com/sufani/SOAR-EDR-Automation-for-Threat-Detection-and-Response/blob/main/images/LimaCharlieGUI.jpeg?raw=true)

### 4. Adding LimaCharlie Sensor
#### Adding LimaCharlie Sensor
Here, I added and configured the LimaCharlie sensor to monitor system activities on the Windows Server.

![LimaCharlie Sensor Installation](https://github.com/sufani/SOAR-EDR-Automation-for-Threat-Detection-and-Response/blob/main/images/LimaAgentInstall.jpeg?raw=true)

### 5. Running and Configuring LaZagne for Attack Simulation
#### Running LaZagne
I ran the LaZagne tool to simulate a credential dumping attack, which was used to test the detection rules configured in LimaCharlie.

![Running LaZagne](https://github.com/sufani/SOAR-EDR-Automation-for-Threat-Detection-and-Response/blob/main/images/LaZagneRun.jpeg?raw=true)

### 6. Monitoring LaZagne Telemetry in LimaCharlie
#### LaZagne Event Detection
This screenshot displays the telemetry data from the LaZagne tool that LimaCharlie captured, showing the command line execution and process details for further analysis.

![LaZagne Event Telemetry](https://github.com/sufani/SOAR-EDR-Automation-for-Threat-Detection-and-Response/blob/main/images/LaZagneEvent.jpeg?raw=true)

### 7. Creating Detection Rules for LaZagne and Other Attacks
#### Detection Rule for LaZagne
A detection rule was created for LaZagne to alert whenever the tool is executed. This ensures quick detection of this and similar tools on the network.

![Detection Rules](https://github.com/sufani/SOAR-EDR-Automation-for-Threat-Detection-and-Response/blob/main/images/Rules.jpeg?raw=true)

### 8. Configuring the SOAR Playbook in Tines
#### SOAR Playbook Configuration
Tines was used to orchestrate automated responses. This step involved configuring Tines to retrieve detection alerts and trigger subsequent actions, such as sending Slack messages and isolating compromised endpoints.

![SOAR Playbook](https://github.com/sufani/SOAR-EDR-Automation-for-Threat-Detection-and-Response/blob/main/images/SOARbuild.jpeg?raw=true)

### 9. Automating Alerts in Slack
#### Slack Alert Setup
Once a threat was detected, an alert was automatically sent to Slack, containing relevant information such as process names and file paths. This alert serves as a critical component of the automated response workflow.

![Slack Alert](https://github.com/sufani/SOAR-EDR-Automation-for-Threat-Detection-and-Response/blob/main/images/SlacklAlert.jpeg?raw=true)

### 10. Automated Email Alerts
#### Email Alert Setup
Similar to Slack, an email alert was sent automatically to the relevant personnel with all the necessary information to investigate and respond to the threat.

![Email Alert](https://github.com/sufani/SOAR-EDR-Automation-for-Threat-Detection-and-Response/blob/main/images/EmailAlert.jpeg?raw=true)

### 11. User Prompt for Machine Isolation
#### User Prompt for Isolation Decision
A user prompt was incorporated in Tines to ask the responder whether to isolate the machine or not. The prompt provides a decision-making option based on the detection details and the context of the alert.

![User Prompt](https://github.com/sufani/SOAR-EDR-Automation-for-Threat-Detection-and-Response/blob/main/images/UserInput.jpeg?raw=true)

### 12. Isolating the Compromised Machine (Ping Failure)
#### Isolation of Compromised Machine
This screenshot shows the moment when the compromised machine was isolated. As a result, the machine’s network connection failed, as shown in the ping results, confirming the isolation.

![Ping Failure Simulation](https://github.com/sufani/SOAR-EDR-Automation-for-Threat-Detection-and-Response/blob/main/images/PingFailure.jpeg?raw=true)

### 13. Isolating the Compromised Machine Automatically
#### Automatic Isolation of Compromised Machine
Based on the detection, the compromised machine was automatically isolated, as seen in LimaCharlie’s isolation status, ensuring containment of the threat.

![Auto Isolation](https://github.com/sufani/SOAR-EDR-Automation-for-Threat-Detection-and-Response/blob/main/images/IsolatedAuto.jpeg?raw=true)

### 14. Isolation Status and Confirmation
#### Confirmation of Isolation Status
The isolation status of the endpoint was confirmed, showing that the machine was successfully isolated from the network as part of the automated response process.

![Isolation Status](https://github.com/sufani/SOAR-EDR-Automation-for-Threat-Detection-and-Response/blob/main/images/IsolationStatus.jpeg?raw=true)

### 15. Full Workflow Execution
#### Complete SOAR EDR Workflow
The full workflow was tested, from detection to isolation, with Tines orchestrating the entire process. Alerts were sent to Slack and email, while LimaCharlie handled telemetry collection and isolation commands.

![Full Workflow](https://github.com/sufani/SOAR-EDR-Automation-for-Threat-Detection-and-Response/blob/main/images/FullWorkflow.jpeg?raw=true)
