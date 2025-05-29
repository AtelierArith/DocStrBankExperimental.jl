```
aws_mqtt_client_connection_set_connection_interruption_handlers(connection, on_interrupted, on_interrupted_ud, on_resumed, on_resumed_ud)
```

Sets the callbacks to call when a connection is interrupted and resumed.

# Arguments

  * `connection`:[in] The connection object
  * `on_interrupted`:[in] The function to call when a connection is lost
  * `on_interrupted_ud`:[in] Userdata for on_interrupted
  * `on_resumed`:[in] The function to call when a connection is resumed (if clean_session is true, calling [`aws_mqtt_resubscribe_existing_topics`](@ref) is suggested)
  * `on_resumed_ud`:[in] Userdata for on_resumed

### Prototype

```c
int aws_mqtt_client_connection_set_connection_interruption_handlers( struct aws_mqtt_client_connection *connection, aws_mqtt_client_on_connection_interrupted_fn *on_interrupted, void *on_interrupted_ud, aws_mqtt_client_on_connection_resumed_fn *on_resumed, void *on_resumed_ud);
```
