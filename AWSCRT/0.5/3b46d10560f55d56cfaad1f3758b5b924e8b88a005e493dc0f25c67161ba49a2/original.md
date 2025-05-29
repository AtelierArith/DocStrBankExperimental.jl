```
on_connection_resumed(
    connection::MQTTConnection,
    return_code::aws_mqtt_connect_return_code,
    session_present::Bool,
)
```

A callback invoked whenever the MQTT connection is automatically resumed.

Arguments:

  * `connection (MQTTConnection)`: The connection.
  * `return_code (aws_mqtt_connect_return_code)`: Connect return code received from the server.
  * `session_present (Bool)`: `true` if resuming existing session. `false` if new session. Note that the server has forgotten all previous subscriptions if this is `false`. Subscriptions can be re-established via [`resubscribe_existing_topics`](@ref).

!!! note
    All callbacks are run concurrently. Your callback implementations must be thread-safe. There is no concurrency limit.

