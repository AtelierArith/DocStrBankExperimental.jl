```
aws_mqtt_client_connection_publish(connection, topic, qos, retain, payload, on_complete, userdata)
```

Send a PUBLISH packet over connection.

# Arguments

  * `connection`:[in] The connection to publish on
  * `topic`:[in] The topic to publish on
  * `qos`:[in] The requested QoS of the packet
  * `retain`:[in] True to have the server save the packet, and send to all new subscriptions matching topic
  * `payload`:[in] The data to send as the payload of the publish
  * `on_complete`:[in] (nullable) For QoS 0, called as soon as the packet is sent For QoS 1, called when PUBACK is received For QoS 2, called when PUBCOMP is received
  * `user_data`:[in] (nullable) Passed to on_complete

# Returns

The packet id of the publish packet if successfully sent, otherwise 0.

### Prototype

```c
uint16_t aws_mqtt_client_connection_publish( struct aws_mqtt_client_connection *connection, const struct aws_byte_cursor *topic, enum aws_mqtt_qos qos, bool retain, const struct aws_byte_cursor *payload, aws_mqtt_op_complete_fn *on_complete, void *userdata);
```
