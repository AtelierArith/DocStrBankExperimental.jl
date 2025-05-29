```
publish_async(client::Client, topic::String, payload...;
   dup::Bool=false,
   qos::QOS=QOS_0,
   retain::Bool=false)
```

Pulishes a message with the specified parameters. Returns a `Future` object that contains `nothing` on success and an exception on failure.
