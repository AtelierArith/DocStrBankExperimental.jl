```
notify_register(protocol::MQTTProtocol, aid::String; kwargs...)
```

Notify the `protocol` MQTT client that a new agent with `aid` has been registered. 

Registration expects a kwarg `topics` to subscribe the agent to.  If any topic is not yet subscribed by the client `subscribe` is called for it.
