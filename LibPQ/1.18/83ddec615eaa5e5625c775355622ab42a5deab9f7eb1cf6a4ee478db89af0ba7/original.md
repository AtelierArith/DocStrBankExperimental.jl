```
prepare(jl_conn::Connection, query::AbstractString) -> Statement
```

Create a prepared statement on the PostgreSQL server using libpq. The statement is given an generated unique name using [`unique_id`](@ref).

!!! note
    Currently the statement is not explicitly deallocated, but it is deallocated at the end of session per the [PostgreSQL documentation on DEALLOCATE](https://www.postgresql.org/docs/10/sql-deallocate.html).

