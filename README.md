# New employee onboarding BOT

This Python code is an example of some of the Webex messaging services you can implement for new employees

## Overview

The script follows these steps:

1. Check if a there is a new employee

    Modern [SCIM 2 API](https://developer.webex.com/admin/docs/scim-2-overview) is being used, instead of the traditional [People API](https://developer.webex.com/admin/docs/api/v1/people).

    In this example, an employee with Postal Code = 'E' is a new employee. This has been taking from a real case scenario, where this was the most convenient way for the customer to identify new employees in Active Directory. Normally, you would use [Custom Attributes](https://help.webex.com/en-us/article/nxrfr9v/User-attributes-in-Control-Hub) instead.

   The script checks for new employees once a day, and the Service App access token will also be renewed every 24 hours.

2. Add the new user(s) to a Main Webex space. This space can be used for announcements, corporate communications, etc.

3. Send a 1:1 welcome Webex message to the users

All these actions are tracked by sending messages to a Reporting Webex space, and all messages are sent by a BOT

## Setup

1. Create a BOT in your Webex ORG, it will be used to send all the messages. Save the BOT token value, you will need it later.

2. Create a Service App in your Webex ORG, save _Client ID_ and _Client Secret_ values. Only this scope is needed: _identity:people_read_.

Authorize your new Service App on Control Hub, go back to your Service App setup page, now you should see there your Access and Refresh Token. Save the Refresh Token value, you will need it later.


3. Clone this repository:

    ```sh
    git clone https://github.com/wxsd-sales/employee-onboarding-bot.git 
    ````

4. Create and activate a Virtual Environment:

    For Windows:
    ```sh
    python -m venv venv
    venv\Scripts\activate
    ````

    For Mac:
    ```sh
    python3 -m venv venv
    source venv/bin/activate
    ```

5. Install dependencies
    ```sh
    pip install -r requirements.txt
    ````
6. Configure your Environment variables
    
    Rename the .env.example file to .env, and fill in your values:


    BOT_TOKEN=`<your bot token>`

    SERVICE_APP_CLIENT_ID=`<your Service App Client ID>`
    
    SERVICE_APP_CLIENT_SECRET=`<your Service App Client Secret>`
    
    SERVICE_APP_REFRESH_TOKEN=`<_your Service App Refresh Token_>`
    
    MAIN_ROOM_ID=`<Room ID for the Main room where all new employees are added>`
    
    REPORTING_ROOM_ID=`<Room ID for the Reporting room>`
    
    ORG_ID=`<Your Webex ORG ID>`


## License

All contents are licensed under the MIT license. Please see [license](https://github.com/wxsd-sales/video-cc-widget-lit/blob/main/LICENSE) for details.


## Disclaimer
Everything included is for demo and Proof of Concept purposes only. Use of the site is solely at your own risk. This site may contain links to third party content, which we do not warrant, endorse, or assume liability for. These demos are for Cisco Webex use cases, but are not Official Cisco Webex Branded demos.

## Questions
Please contact the WXSD team at [wxsd@external.cisco.com](mailto:wxsd@external.cisco.com?subject=custom-dial-macro) for questions. Or, if you're a Cisco internal employee, reach out to us on the Webex App via our bot (globalexpert@webex.bot). In the "Engagement Type" field, choose the "API/SDK Proof of Concept Integration Development" option to make sure you reach our team. 
