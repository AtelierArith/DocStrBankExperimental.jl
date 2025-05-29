```
subscribe(client::ShadowClient, topic::String, qos::aws_mqtt_qos, callback::OnMessage)
```

Subscribes to the given `topic` (must contain a leading forward slash (`/`)) under the given shadow document.

Arguments:

  * `client (ShadowClient)`: Shadow client to use.
  * `topic (String)`: Subscribe to this topic filter, which may include wildcards, under the given shadow document.
  * `qos (aws_mqtt_qos)`: Maximum requested QoS that the server may use when sending messages to the client. The server may grant a lower QoS in the SUBACK (see returned task).
  * `callback (OnMessage)`: Callback invoked when a message is received. See [`OnMessage`](@ref) for the required signature.

Returns a task and the ID of the SUBSCRIBE packet. The task completes when a SUBACK is received from the server.

If successful, the task will contain a dict with the following members:

  * `:packet_id (Int)`: ID of the SUBSCRIBE packet being acknowledged.
  * `:topic (String)`: Topic filter of the SUBSCRIBE packet being acknowledged.
  * `:qos (aws_mqtt_qos)`: Maximum QoS that was granted by the server. This may be lower than the requested QoS.

If unsuccessful, the task contains an exception.

If there is no MQTT connection or network connection, the task may wait forever.

Throws if the SUBSCRIBE packet could not be sent.
