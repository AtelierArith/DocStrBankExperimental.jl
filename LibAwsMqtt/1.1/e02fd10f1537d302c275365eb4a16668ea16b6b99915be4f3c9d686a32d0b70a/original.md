```
aws_mqtt_client_connection_set_on_any_publish_handler(connection, on_any_publish, on_any_publish_ud)
```

Sets the callback to call whenever ANY publish packet is received. Only safe to set when connection is not connected.

# Arguments

  * `connection`:[in] The connection object
  * `on_any_publish`:[in] The function to call when a publish is received (pass NULL to unset)
  * `on_any_publish_ud`:[in] Userdata for on_any_publish

### Prototype

```c
int aws_mqtt_client_connection_set_on_any_publish_handler( struct aws_mqtt_client_connection *connection, aws_mqtt_client_publish_received_fn *on_any_publish, void *on_any_publish_ud);
```
