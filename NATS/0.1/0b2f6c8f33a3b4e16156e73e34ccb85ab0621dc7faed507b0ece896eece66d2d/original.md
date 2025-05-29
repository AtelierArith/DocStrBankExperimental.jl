```julia
request(connection, nreplies, subject; ...)
request(connection, nreplies, subject, data; timer)

```

Requests for multiple replies. Vector of messages is returned after receiving `nreplies` replies or timer expired. Can return less messages than specified (also empty array if timeout occurs), errors are not filtered.

Optional keyword arguments are:

  * `timer`: empty vector will be returned if no replies received until `timer` expires

# Examples

```julia-repl
julia> request(connection, 2, "help.please"; timer = Timer(0))
NATS.Msg[]
```
