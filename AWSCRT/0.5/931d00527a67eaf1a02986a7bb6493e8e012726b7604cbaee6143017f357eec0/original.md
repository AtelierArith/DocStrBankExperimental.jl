```
unsubscribe(connection::MQTTConnection, topic::String)
```

Unsubscribe from a topic filter (async). The client sends an UNSUBSCRIBE packet, and the server responds with an UNSUBACK.

Arguments:

  * `connection (MQTTConnection)`: Connection to use.
  * `topic (String)`: Unsubscribe from this topic filter.

Returns a task and the ID of the UNSUBSCRIBE packet. The task completes when an UNSUBACK is received from the server.

If successful, the task will contain a dict with the following members:

  * `:packet_id (Int)`: ID of the UNSUBSCRIBE packet being acknowledged.

If unsuccessful, the task will throw an exception.

If there is no MQTT connection or network connection, the task may wait forever.

Throws if the UNSUBSCRIBE packet could not be sent.
