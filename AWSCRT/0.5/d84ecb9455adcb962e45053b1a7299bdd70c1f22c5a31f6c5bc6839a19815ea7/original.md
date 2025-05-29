```
publish(connection::MQTTConnection, topic::String, payload::String, qos::aws_mqtt_qos, retain::Bool = false)
```

Publish message (async). If the device is offline, the PUBLISH packet will be sent once the connection resumes.

Arguments:

  * `connection (MQTTConnection)`: Connection to use.
  * `topic (String)`: Topic name.
  * `payload (String)`: Contents of message.
  * `qos (aws_mqtt_qos)`: Maximum requested QoS that the server may use when sending messages to the client. The server may grant a lower QoS in the SUBACK (see returned task).
  * `retain (Bool)`: If `true`, the server will store the message and its QoS so that it can be delivered to future subscribers whose subscriptions match its topic name.

Returns a task and the ID of the PUBLISH packet. The QoS determines when the task completes:

  * For QoS 0, completes as soon as the packet is sent.
  * For QoS 1, completes when PUBACK is received.
  * For QoS 2, completes when PUBCOMP is received.

If successful, the task will contain a dict with the following members:

  * `:packet_id (Int)`: ID of the PUBLISH packet that is complete.

If unsuccessful, the task will throw an exception.

If there is no MQTT connection or network connection, the task may wait forever.

Throws if the PUBLISH packet could not be sent.
