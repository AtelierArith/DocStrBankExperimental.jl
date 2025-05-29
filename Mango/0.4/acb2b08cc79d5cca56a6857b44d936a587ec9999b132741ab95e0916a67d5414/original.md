```
subscribe_send(role::Role, handler::Function)
```

Subscribe a `send_message` hook in function (signature, (role, content, receiver*id, receiver*addr; kwargs...)) to the message sending. The hook in function will be called every time a message is sent by the agent.
