```
aws_mqtt_client_connection_unsubscribe(connection, topic_filter, on_unsuback, on_unsuback_ud)
```

Unsubscribe to a topic filter.

# Arguments

  * `connection`:[in] The connection to unsubscribe on
  * `topic_filter`:[in] The topic filter to unsubscribe on. This resource must persist until on_unsuback.
  * `on_unsuback`:[in] (nullable) Called when a UNSUBACK has been received from the server and the subscription is removed
  * `on_unsuback_ud`:[in] (nullable) Passed to on_unsuback

# Returns

The packet id of the unsubscribe packet if successfully sent, otherwise 0.

### Prototype

```c
uint16_t aws_mqtt_client_connection_unsubscribe( struct aws_mqtt_client_connection *connection, const struct aws_byte_cursor *topic_filter, aws_mqtt_op_complete_fn *on_unsuback, void *on_unsuback_ud);
```
