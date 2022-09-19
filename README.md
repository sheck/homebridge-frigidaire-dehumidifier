[![NPM Version](https://img.shields.io/npm/v/homebridge-frigidaire-dehumidifier.svg?style=flat-square)](https://www.npmjs.com/package/homebridge-frigidaire-dehumidifier)


<p align="center">
 
<img src="https://github.com/homebridge/branding/raw/master/logos/homebridge-wordmark-logo-vertical.png" width="150">

</p>


# Homebridge Plug-In for Frigidaire Dehumidifier
An Homebridge plug-in to integrate the Frigidaire's connected dehumidifier with HomeKit. It monitors and control devices via the Frigidaire unofficial cloud API. Thanks to the Frigidaire Python API  https://github.com/bm1549/frigidaire developer, this module uses the logic gain from reviewing those libraries/code.

## Limitation:
* This module will poll for the status of the various components based frequency provided in the configuration file. No realtime notification is provided.


## Configuration options

| Attributes        | Description                                                                                                              |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------ |
| username              | Frigidaire username. This is a required value.                    |
| password              | Frigidaire password. This is a required value.                                                                 |
| deviceRefresh        | Polling interval to obtain status of Frigidaire appliance, provided in seconds. Default to <i>90</i> seconds, this is an optional value. <b>Please note:</b> Small values may cause account lock or frequent API errors.                                                                    |
| dehumidifierMode          | Homekit only has two mode dehumidifying modes "Auto" and "Dehumidifying". When "Dehumidifying" is selected in Homekit the selection is map to a single specific Frigidaire appliance mode such <i>Quiet</i>, <i>Dry</i> and <i>Continuous</i>. The default mode for "Dehumidifying" is Frigidaire <i>Dry</i> mode, this an optional value.  
| enableAirPurifier | Create additional tile for Air purifier/Ionizer functionality. Default to <i>true</i>, this is an optional value.                     
| sessionKeyRefresh        | Refresh interval to obtain new a Frigidaire appliance key. The value is provided in hours and default to <i>9</i> hours, this is an optional value. <b>Please note:</b> Session key are valid for 12 hours, the plug-in does check if a valid key is present before each operation and automatically tries to re-login. This value is a proactive to prevent error from appearing in logs due to expiring key and these automatically re-logins.                                      
| excludedDevices         | Devices to suppress from HomeKit. This is an optional value. | |




Example configuration is below, with Frigidaire dehumidifer mode set to <i>Quiet</i> and Air purifier/Fresher/Ionizer set tile set to display in Homekit. 

```javascript
...

"platforms": [
{
    "name": "FrigidaireAppliance",
    "auth": {
        "username": "<username>",
        "password": "<password>"
      },
      "deviceRefresh": 90,
      "dehumidifierMode": 9,
      "enableAirPurifier": true,
      "platform": "FrigidaireAppliance"
}
...]
