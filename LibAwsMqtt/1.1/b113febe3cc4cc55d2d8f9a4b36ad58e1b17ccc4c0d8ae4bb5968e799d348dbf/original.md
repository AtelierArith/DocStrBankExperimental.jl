```
aws_mqtt_client_connection_set_connection_closed_handler(connection, on_closed, on_closed_ud)
```

Sets the callback to call when the connection is closed normally by user request. This is different than the connection interrupted or lost, this only covers successful closure.

# Arguments

  * `connection`:[in] The connection object
  * `on_closed`:[in] The function to call when a connection is closed
  * `on_closed_ud`:[in] Userdata for on_closed

### Prototype

```c
int aws_mqtt_client_connection_set_connection_closed_handler( struct aws_mqtt_client_connection *connection, aws_mqtt_client_on_connection_closed_fn *on_closed, void *on_closed_ud);
```
