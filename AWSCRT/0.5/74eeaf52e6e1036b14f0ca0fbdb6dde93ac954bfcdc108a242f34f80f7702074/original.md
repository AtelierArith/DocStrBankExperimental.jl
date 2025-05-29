```
publish_current_state(sf::ShadowFramework; include_version::Bool = true)
```

Publishes the current state of the shadow document.

Arguments:

  * `include_version (Bool)`: Includes the version of the shadow document if this is `true`. You may want to exclude the version if you don't know what the broker's version is.

Returns a task and the ID of the PUBLISH packet. The QoS determines when the task completes:

  * For QoS 0, completes as soon as the packet is sent.
  * For QoS 1, completes when PUBACK is received.
  * For QoS 2, completes when PUBCOMP is received.

If successful, the task will contain a dict with the following members:

  * `:packet_id (Int)`: ID of the PUBLISH packet that is complete.

If unsuccessful, the task will throw an exception.

If there is no MQTT connection or network connection, the task may wait forever.

Throws if the PUBLISH packet could not be sent.
