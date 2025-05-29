```
subscribe(client::Client, topic::String, on_msg::Function; qos::UInt8=QOS_0)
```

Subscribe to a topic.

# Arguments

  * `client::Client`: The MQTT client.
  * `topic::String`: The topic to subscribe to.
  * `on_msg::Function`: The function to call when a message is received on the topic.
  * `qos::UInt8`: The quality of service level to use for the subscription. Default is 0.

# Examples

```julia
subscribe(client, "my/topic", on_msg)
```
