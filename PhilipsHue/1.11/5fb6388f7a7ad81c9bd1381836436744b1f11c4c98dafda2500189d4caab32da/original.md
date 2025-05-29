```
getbridgeinfo(bridge[, category::String])
```

Get some information from the bridge. Category can be one of:

  * "lights" resource which contains all the light resources
  * "groups" resource which contains all the groups
  * "config" resource which contains all the configuration items
  * "schedules" which contains all the schedules
  * "scenes" which contains all the scenes
  * "sensors" which contains all the sensors
  * "rules" which contains all the rules

Default is "config".
