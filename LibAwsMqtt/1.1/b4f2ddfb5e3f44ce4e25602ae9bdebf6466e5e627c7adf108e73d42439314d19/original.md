```
aws_mqtt_client_connection_set_connection_termination_handler(connection, on_termination, on_termination_ud)
```

Sets the callback to call on a connection destruction.

# Arguments

  * `connection`:[in] The connection object.
  * `on_termination`:[in] The function to call when a connection is destroyed.
  * `on_termination_ud`:[in] Userdata for on_termination.

### Prototype

```c
int aws_mqtt_client_connection_set_connection_termination_handler( struct aws_mqtt_client_connection *connection, aws_mqtt_client_on_connection_termination_fn *on_termination, void *on_termination_ud);
```
