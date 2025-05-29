```
function receive(fn::Function, pd::Process)
```

Execute `fn(msg)` for every message `msg` delivered to the `pd` Process.

Return if a `Shutdown` control message is received.
