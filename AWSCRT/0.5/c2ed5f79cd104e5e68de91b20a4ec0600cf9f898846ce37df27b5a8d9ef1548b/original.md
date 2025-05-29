```
Will(
    topic::String,
    qos::aws_mqtt_qos,
    payload::String,
    retain::Bool,
)
```

A Will message is published by the server if a client is lost unexpectedly.

The Will message is stored on the server when a client connects. It is published if the client connection is lost without the server receiving a DISCONNECT packet.

[MQTT-3.1.2-8]

Arguments:

  * `topic (String)`: Topic to publish Will message on.
  * `qos (aws_mqtt_qos)`: QoS used when publishing the Will message.
  * `payload (String)`: Content of Will message.
  * `retain (Bool)`: Whether the Will message is to be retained when it is published.
