```
aws_mqtt_client_connection_subscribe_multiple(connection, topic_filters, on_suback, on_suback_ud)
```

Subscribe to topic filters. on_publish will be called when a PUBLISH matching each topic_filter is received.

# Arguments

  * `connection`:[in] The connection to subscribe on
  * `topic_filters`:[in] An array_list of [`aws_mqtt_topic_subscription`](@ref) (NOT pointers) describing the requests.
  * `on_suback`:[in] (nullable) Called when a SUBACK has been received from the server and the subscription is complete. Broker may fail one of the topics, check the qos in [`aws_mqtt_topic_subscription`](@ref) from the callback
  * `on_suback_ud`:[in] (nullable) Passed to on_suback

# Returns

The packet id of the subscribe packet if successfully sent, otherwise 0.

### Prototype

```c
uint16_t aws_mqtt_client_connection_subscribe_multiple( struct aws_mqtt_client_connection *connection, const struct aws_array_list *topic_filters, aws_mqtt_suback_multi_fn *on_suback, void *on_suback_ud);
```
