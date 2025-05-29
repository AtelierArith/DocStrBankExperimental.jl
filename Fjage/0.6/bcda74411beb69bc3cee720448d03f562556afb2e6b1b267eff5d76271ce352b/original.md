```
receive(a::Agent, timeout::Int=0; priority)
receive(a::Agent, filt, timeout::Int=0; priority)
```

Receive a message, optionally matching the specified filter. The call blocks for at most `timeout` milliseconds, if a message is not available. If multiple `receive()` calls are concurrently active, the `priority` determines which call gets the message. Only one of the active `receive()` calls will receive the message. Returns a message or `nothing`.

If a filter `filt` is specified, only messages matching the filter trigger this behavior. A filter may be a message class or a function that takes the message as an argument and returns `true` to accept, `false` to reject.

Lower priority numbers indicate a higher priority.
