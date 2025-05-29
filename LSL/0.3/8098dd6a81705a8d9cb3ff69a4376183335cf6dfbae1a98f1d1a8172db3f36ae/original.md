```
session_id(info::StreamInfo)
```

Return session ID for the given stream.

The session id is an optional human-assigned identifier of the recording session. While it is rarely used, it can be used to prevent concurrent recording activitites in the same sub-network (e.g., in multiple experiment areas) from seeing each other's streams (assigned via a configuration file by the experimenter, see Network Connectivity on the LSL wiki).
