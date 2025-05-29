```
status(jl_conn::Connection) -> libpq_c.ConnStatusType
```

Return the status of the PostgreSQL database connection according to libpq. Only `CONNECTION_OK` and `CONNECTION_BAD` are valid for blocking connections, and only blocking connections are supported right now.

See also: [`error_message`](@ref)
