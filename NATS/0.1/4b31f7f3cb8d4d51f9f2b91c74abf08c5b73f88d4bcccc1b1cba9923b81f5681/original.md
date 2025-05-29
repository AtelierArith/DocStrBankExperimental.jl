```julia
with_connection(f, nc)

```

Create scope with ambient context connection, in which connection argument might be skipped during invocation of functions.

Usage:

```
    nc = NATS.connect()
    with_connection(nc) do
        publish("some.subject") # No `connection` argument.
    end
```
