```
resubscribe_existing_topics(connection::MQTTConnection)
```

Subscribe again to all current topics. This is to help when resuming a connection with a clean session.

Returns a task and the ID of the SUBSCRIBE packet. The task completes when a SUBACK is received from the server.

If successful, the task will contain a dict with the following members:

  * `:packet_id (Int)`: ID of the SUBSCRIBE packet being acknowledged.
  * `:topics (Vector{Tuple{Union{String,Nothing},aws_mqtt_qos}})`: Topic filter of the SUBSCRIBE packet being acknowledged and its QoS level. The topic will be `nothing` if the topic failed to resubscribe. The vector will be empty if there were no topics to resubscribe.

If unsuccessful, the task contains an exception.

Throws if the SUBSCRIBE packet could not be sent.
