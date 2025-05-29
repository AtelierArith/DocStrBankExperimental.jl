```
publish(client::ShadowClient, topic::String, payload::String, qos::aws_mqtt_qos)
```

Publishes the payload to the topic under the configured shadow topic.

Arguments:

  * `client (ShadowClient)`: Shadow client to use.
  * `topic (String)`: Topic name, not including the shadow topic prefix. E.g. `/get`.
  * `payload (String)`: Message contents.
  * `qos (aws_mqtt_qos)`: Maximum requested QoS that the server may use when sending messages to the client. The server may grant a lower QoS in the SUBACK (see returned task).

Returns a task and the ID of the PUBLISH packet. The QoS determines when the task completes:

  * For QoS 0, completes as soon as the packet is sent.
  * For QoS 1, completes when PUBACK is received.
  * For QoS 2, completes when PUBCOMP is received.

If successful, the task will contain a dict with the following members:

  * `:packet_id (Int)`: ID of the PUBLISH packet that is complete.

If unsuccessful, the task will throw an exception.

If there is no MQTT connection or network connection, the task may wait forever.

Throws if the PUBLISH packet could not be sent.
