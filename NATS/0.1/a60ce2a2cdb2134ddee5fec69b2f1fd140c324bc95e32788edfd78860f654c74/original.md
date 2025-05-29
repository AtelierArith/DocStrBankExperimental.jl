```julia
request(connection, subject; ...)
request(connection, subject, data; timer)

```

Send NATS [Request-Reply](https://docs.nats.io/nats-concepts/core-nats/reqreply) message.

Default timeout is 5.0 seconds which can be overriden by passing `timer`. It can be configured globally with `NATS_REQUEST_TIMEOUT_SECONDS` env variable.

Optional keyword arguments are:

  * `timer`: error will be thrown if no replies received until `timer` expires

# Examples

```julia-repl
julia> NATS.request(connection, "help.please")
NATS.Msg("l9dKWs86", "7Nsv5SZs", nothing, "", "OK, I CAN HELP!!!")

julia> request(connection, "help.please"; timer = Timer(0))
ERROR: No replies received.
```
