```
on_connection_interrupted(
    connection::MQTTConnection,
    error_code::Int,
)
```

A callback invoked whenever the MQTT connection is lost. The MQTT client will automatically attempt to reconnect.

Arguments:

  * `connection (MQTTConnection)`: The connection.
  * `error_code (Int)`: Error which caused connection loss.

!!! note
    All callbacks are run concurrently. Your callback implementations must be thread-safe. There is no concurrency limit.

