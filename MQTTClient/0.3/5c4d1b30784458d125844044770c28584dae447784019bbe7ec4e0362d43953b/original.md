```
subscribe_async(client::Client, topic::String, on_msg::Function; qos::UInt8=QOS_0)
```

Subscribe to a topic asynchronously.

# Arguments

  * `client::Client`: The MQTT client.
  * `topic::String`: The topic to subscribe to.
  * `on_msg::Function`: The function to call when a message is received on the topic.
  * `qos::UInt8`: The quality of service level to use for the subscription. Default is 0.

# Returns

  * `Future`: A future that can be used to wait for the subscription to complete.

# Examples

```julia
future = subscribe_async(client, "my/topic", on_msg; qos=QOS_2)
```
