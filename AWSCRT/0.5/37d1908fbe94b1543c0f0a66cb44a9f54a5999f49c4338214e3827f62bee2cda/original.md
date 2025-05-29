```
subscribe(client::ShadowClient, qos::aws_mqtt_qos, callback::OnShadowMessage)
```

Subscribes to all topics under the given shadow document using a wildcard, including but not limited to:

  * `/get/accepted`
  * `/get/rejected`
  * `/update/delta`
  * `/update/accepted`
  * `/update/documents`
  * `/update/rejected`
  * `/delete/accepted`
  * `/delete/rejected`

Arguments:

  * `client (ShadowClient)`: Shadow client to use.
  * `qos (aws_mqtt_qos)`: Maximum requested QoS that the server may use when sending messages to the client. The server may grant a lower QoS in the SUBACK (see returned task).
  * `callback (OnShadowMessage)`: Callback invoked when message received. See [`OnShadowMessage`](@ref) for the required signature.

Returns a task which completes when the tasks from each [`subscribe`](@ref) call complete. Also returns a collection containing the packet ID from each [`subscribe`](@ref) call.
