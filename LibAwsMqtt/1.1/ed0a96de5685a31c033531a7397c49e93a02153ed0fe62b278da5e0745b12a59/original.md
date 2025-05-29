```
aws_mqtt_client_connection_use_websockets(connection, transformer, transformer_ud, validator, validator_ud)
```

Use MQTT over websockets when connecting. Requires the MQTT_WITH_WEBSOCKETS build option.

In this scenario, an HTTP connection is established, which is then upgraded to a websocket connection, which is then used to send MQTT data.

# Arguments

  * `connection`:[in] The connection object.
  * `transformer`:[in] [optional] Function that may transform the websocket handshake request. See [`aws_mqtt_transform_websocket_handshake_fn`](@ref) for more info.
  * `transformer_ud`:[in] [optional] Userdata for request_transformer.
  * `validator`:[in] [optional] Function that may reject the websocket handshake response.
  * `validator_ud`:[in] [optional] Userdata for response_validator.

### Prototype

```c
int aws_mqtt_client_connection_use_websockets( struct aws_mqtt_client_connection *connection, aws_mqtt_transform_websocket_handshake_fn *transformer, void *transformer_ud, aws_mqtt_validate_websocket_handshake_fn *validator, void *validator_ud);
```
