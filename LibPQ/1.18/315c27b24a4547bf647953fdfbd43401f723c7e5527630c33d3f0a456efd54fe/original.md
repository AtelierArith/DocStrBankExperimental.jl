```
execute(jl_conn::Connection, copyin::CopyIn, args...;
    throw_error::Bool=true, kwargs...
) -> Result
```

Runs [`execute`](@ref execute(::Connection, ::String)) on `copyin`'s query, then sends `copyin`'s data to the server.

All other arguments are passed through to the `execute` call for the initial query.
