```
aws_mqtt_client_connection_connect(connection, connection_options)
```

Opens the actual connection defined by [`aws_mqtt_client_connection_new`](@ref). Once the connection is opened, on_connack will be called. Only called when connection is disconnected.

# Arguments

  * `connection`:[in] The connection object
  * `connection_options`:[in] Configuration information for the connection attempt

# Returns

AWS_OP_SUCCESS if the connection has been successfully initiated, otherwise AWS_OP_ERR and aws_last_error() will be set.

### Prototype

```c
int aws_mqtt_client_connection_connect( struct aws_mqtt_client_connection *connection, const struct aws_mqtt_connection_options *connection_options);
```
