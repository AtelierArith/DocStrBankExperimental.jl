```
aws_mqtt_client_connection_subscribe(connection, topic_filter, qos, on_publish, on_publish_ud, on_ud_cleanup, on_suback, on_suback_ud)
```

Subscribe to a single topic filter. on_publish will be called when a PUBLISH matching topic_filter is received.

# Arguments

  * `connection`:[in] The connection to subscribe on
  * `topic_filter`:[in] The topic filter to subscribe on. This resource must persist until on_suback.
  * `qos`:[in] The maximum QoS of messages to receive
  * `on_publish`:[in] (nullable) Called when a PUBLISH packet matching topic_filter is received
  * `on_publish_ud`:[in] (nullable) Passed to on_publish
  * `on_ud_cleanup`:[in] (nullable) Called when a subscription is removed, on_publish_ud is passed.
  * `on_suback`:[in] (nullable) Called when a SUBACK has been received from the server and the subscription is complete
  * `on_suback_ud`:[in] (nullable) Passed to on_suback

# Returns

The packet id of the subscribe packet if successfully sent, otherwise 0.

### Prototype

```c
uint16_t aws_mqtt_client_connection_subscribe( struct aws_mqtt_client_connection *connection, const struct aws_byte_cursor *topic_filter, enum aws_mqtt_qos qos, aws_mqtt_client_publish_received_fn *on_publish, void *on_publish_ud, aws_mqtt_userdata_cleanup_fn *on_ud_cleanup, aws_mqtt_suback_fn *on_suback, void *on_suback_ud);
```
