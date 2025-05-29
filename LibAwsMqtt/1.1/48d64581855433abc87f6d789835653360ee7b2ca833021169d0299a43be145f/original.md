```
aws_mqtt_client_connection_reconnect(connection, on_connection_complete, userdata)
```

DEPRECATED Opens the actual connection defined by [`aws_mqtt_client_connection_new`](@ref). Once the connection is opened, on_connack will be called.

Must be called on a connection that has previously been open, as the parameters passed during the last connection will be reused.

# Arguments

  * `connection`:[in] The connection object
  * `on_connection_complete`:[in] The callback to fire when the connection attempt completes
  * `userdata`:[in] (nullable) Passed to the userdata param of on_connection_complete

# Returns

AWS_OP_SUCCESS if the connection has been successfully initiated, otherwise AWS_OP_ERR and aws_last_error() will be set.

### Prototype

```c
int aws_mqtt_client_connection_reconnect( struct aws_mqtt_client_connection *connection, aws_mqtt_client_on_connection_complete_fn *on_connection_complete, void *userdata);
```
