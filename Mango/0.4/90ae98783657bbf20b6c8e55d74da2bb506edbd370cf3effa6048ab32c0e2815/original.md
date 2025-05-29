```
reply_to(
agent::AgentInterface,
content::Any,
received_meta::AbstractDict,
```

)

Convenience method to reply to a received message using the meta the agent received. This reduces the regular `send_message` as response `send_message(agent, "Pong", AgentAddress(aid=meta["sender_id"], address=meta["sender_addr"]))` to `reply_to(agent, "Pong", meta)`

Furthermore it guarantees that agent address (including the tracking id, which is part of the address!) is correctly passed to the mango container.
