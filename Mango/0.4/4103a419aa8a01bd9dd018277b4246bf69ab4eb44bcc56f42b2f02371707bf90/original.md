```
start(container)
```

Start the container. It is recommended to use [`activate`](@ref) instead of starting manually.

What exactly happend highly depends on the protocol and the container implmentation. For example, for TCP the container binds on IP and port, and the listening loop started.
