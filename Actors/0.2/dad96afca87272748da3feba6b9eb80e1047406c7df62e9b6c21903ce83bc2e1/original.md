```
send(lk::Link, msg...)
send(name::Symbol, msg...)
```

Send a message to an actor `lk` (or registered `name`).  `msg...` are communication parameters to the actor's behavior  function.
