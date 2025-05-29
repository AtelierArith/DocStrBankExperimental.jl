```
subscribe_message(role::Role, handler::Function, condition::Function)
```

Subscribe a message handler function (it need to have the signature (role, message, meta)) to the message dispatching. This handler function will be called everytime the given condition function ((message, meta) -> boolean) evaluates to true when a message arrives at the roles agent.
