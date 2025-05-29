```
disconnect(connection::MQTTConnection)
```

Close the connection to the server (async). Returns a task which completes when the connection is closed. If there is no MQTT connection or network connection, the task completes. The task will contain nothing.
