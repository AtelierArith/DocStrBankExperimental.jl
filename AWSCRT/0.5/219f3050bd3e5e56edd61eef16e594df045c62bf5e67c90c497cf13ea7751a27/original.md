```
subscribe(sf::ShadowFramework)
```

Subscribes to the shadow document's topics and begins processing updates. The `sf` is always locked before reading/writing from/to the shadow document. If the remote shadow document does not exist, the local shadow document will be used to create it.

Publishes an initial message to the `/get` topic to synchronize the shadow document with the broker's state. You can call `wait_until_synced(sf)` if you need to wait until this synchronization is done.

Returns a task and the ID of the PUBLISH packet. The QoS determines when the task completes:

  * For QoS 0, completes as soon as the packet is sent.
  * For QoS 1, completes when PUBACK is received.
  * For QoS 2, completes when PUBCOMP is received.

If successful, the task will contain a dict with the following members:

  * `:packet_id (Int)`: ID of the PUBLISH packet that is complete.

If unsuccessful, the task will throw an exception.

If there is no MQTT connection or network connection, the task may wait forever.

Throws if the PUBLISH packet could not be sent.
