```
on_shadow_message(
    shadow_client::ShadowClient,
    topic::String,
    payload::String,
    dup::Bool,
    qos::aws_mqtt_qos,
    retain::Bool,
)
```

A callback invoked when a shadow document message is received.

Arguments:

  * `shadow_client (ShadowClient)`: Shadow client that received the message.
  * `topic (String)`: Topic receiving message.
  * `payload (String)`: Payload of message.
  * `dup (Bool)`: DUP flag. If `true`, this might be re-delivery of an earlier attempt to send the message.
  * `qos (aws_mqtt_qos)`: Maximum requested QoS that the server may use when sending messages to the client. The server may grant a lower QoS in the SUBACK (see returned task).
  * `retain (Bool)`: Retain flag. If `true`, the message was sent as a result of a new subscription being made by the client.

Returns `nothing`.
