```
subscribe(protocol::MQTTProtocol, topic::String; qos::Int=1)
```

Subscribe the MQTT client of the `protocol` to `topic` with the given `qos` setting.

# Returns

The Mosquitto error code and the message id.
