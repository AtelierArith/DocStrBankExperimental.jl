```
aws_mqtt_resubscribe_existing_topics(connection, on_suback, on_suback_ud)
```

Resubscribe to all topics currently subscribed to. This is to help when resuming a connection with a clean session.

# Arguments

  * `connection`:[in] The connection to subscribe on
  * `on_suback`:[in] (nullable) Called when a SUBACK has been received from the server and the subscription is complete
  * `on_suback_ud`:[in] (nullable) Passed to on_suback

# Returns

The packet id of the subscribe packet if successfully sent, otherwise 0 (and aws_last_error() will be set).

### Prototype

```c
uint16_t aws_mqtt_resubscribe_existing_topics( struct aws_mqtt_client_connection *connection, aws_mqtt_suback_multi_fn *on_suback, void *on_suback_ud);
```
