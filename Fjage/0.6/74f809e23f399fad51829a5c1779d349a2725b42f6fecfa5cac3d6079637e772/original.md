```
msg = receive(gw[, filter][, timeout])
```

Receive an incoming message from other agents or topics. Timeout is specified in milliseconds. If no timeout is specified, the call is non-blocking. If a negative timeout is specified, the call is blocking until a message is available.

If a `filter` is specified, only messages matching the filter are retrieved. A filter may be a message type, a message or a function. If it is a message type, only messages of that type or a subtype are retrieved. If it is a message, any message whose `inReplyTo` field is set to the `msgID` of the specified message is retrieved. If it is a function, it must take in a message and return `true` or `false`. A message for which it returns `true` is retrieved.
