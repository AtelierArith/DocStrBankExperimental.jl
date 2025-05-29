```
aws_mqtt_client_connection_disconnect(connection, on_disconnect, userdata)
```

Closes the connection asynchronously, calls the on_disconnect callback. All uncompleted requests (publish/subscribe/unsubscribe) will be cancelled, regardless to the status of clean_session. DISCONNECT packet will be sent, which deletes the will message from server.

# Arguments

  * `connection`:[in] The connection to close
  * `on_disconnect`:[in] (nullable) Callback function to invoke when the connection is completely disconnected.
  * `userdata`:[in] (nullable) passed to on_disconnect

# Returns

AWS_OP_SUCCESS if the connection is open and is being shutdown, otherwise AWS_OP_ERR and aws_last_error() is set.

### Prototype

```c
int aws_mqtt_client_connection_disconnect( struct aws_mqtt_client_connection *connection, aws_mqtt_client_on_disconnect_fn *on_disconnect, void *userdata);
```
