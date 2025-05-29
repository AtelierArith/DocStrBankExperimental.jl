publish(client::Client, topic::String, payload...; dup::Bool=false, qos::QOS=QOS_0, retain::Bool=false)

Waits until the publish is completely acknowledged. Publishes a message with the specified parameters. Returns `nothign` on success and throws an exception on failure.
