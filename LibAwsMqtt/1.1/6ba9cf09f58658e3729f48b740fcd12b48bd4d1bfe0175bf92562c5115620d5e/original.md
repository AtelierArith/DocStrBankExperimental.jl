```
aws_mqtt_client_connection_set_connection_result_handlers(connection, on_connection_success, on_connection_success_ud, on_connection_failure, on_connection_failure_ud)
```

Sets the callbacks to call when a connection succeeds or fails

# Arguments

  * `connection`:[in] The connection object
  * `on_connection_success`:[in] The function to call when a connection is successful or gets resumed
  * `on_connection_success_ud`:[in] Userdata for on_connection_success
  * `on_connection_failure`:[in] The function to call when a connection fails
  * `on_connection_failure_ud`:[in] Userdata for on_connection_failure

### Prototype

```c
int aws_mqtt_client_connection_set_connection_result_handlers( struct aws_mqtt_client_connection *connection, aws_mqtt_client_on_connection_success_fn *on_connection_success, void *on_connection_success_ud, aws_mqtt_client_on_connection_failure_fn *on_connection_failure, void *on_connection_failure_ud);
```
