```
aws_mqtt_client_connection_set_will(connection, topic, qos, retain, payload)
```

Sets the will message to send with the CONNECT packet.

# Arguments

  * `connection`:[in] The connection object
  * `topic`:[in] The topic to publish the will on
  * `qos`:[in] The QoS to publish the will with
  * `retain`:[in] The retain flag to publish the will with
  * `payload`:[in] The data if the will message

### Prototype

```c
int aws_mqtt_client_connection_set_will( struct aws_mqtt_client_connection *connection, const struct aws_byte_cursor *topic, enum aws_mqtt_qos qos, bool retain, const struct aws_byte_cursor *payload);
```
