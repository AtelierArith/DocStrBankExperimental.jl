```
reset!(jl_conn::Connection; throw_error=true)
```

Reset the communication to the PostgreSQL server. The `PGconn` object will be recreated using identical connection parameters.

See [`handle_new_connection`](@ref) for information on the `throw_error` argument.

!!! note
    This function can be called on a connection with status `CONNECTION_BAD`, for example, but cannot be called on a connection that has been closed.

