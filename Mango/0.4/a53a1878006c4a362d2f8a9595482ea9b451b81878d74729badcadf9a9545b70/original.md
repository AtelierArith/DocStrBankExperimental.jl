```
handle_message(agent::Agent, message::Any, meta::Any)
```

Defines a function for an agent, which will be called when a message is dispatched to the agent. This methods will be called with any arriving message (according to the multiple dispatch of julia).
