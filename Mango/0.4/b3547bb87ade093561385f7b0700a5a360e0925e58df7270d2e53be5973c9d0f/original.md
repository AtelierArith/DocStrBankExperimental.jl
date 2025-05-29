```
send_message(
agent::AgentInterface,
content::Any,
agent_address::Address;
kwargs...,
```

)

Send a message with the content `content` to the agent represented by `agent_address`. 

This method will always set a sender_id. Additionally, further keyword arguments can be defined to fill the  internal meta data of the message.
