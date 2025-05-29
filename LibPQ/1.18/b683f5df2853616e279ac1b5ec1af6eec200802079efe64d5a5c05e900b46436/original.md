```
async_execute(
    jl_conn::Connection,
    query::AbstractString,
    [parameters::Union{AbstractVector, Tuple},]
    binary_format::Bool=false,
    kwargs...
) -> AsyncResult
```

Run a query on the PostgreSQL database and return an [`AsyncResult`](@ref).

The `AsyncResult` contains a `Task` which processes a query asynchronously. Calling `fetch` on the `AsyncResult` will return a [`Result`](@ref).

All keyword arguments are the same as [`execute`](@ref) and are passed to the created `Result`.

Only one `AsyncResult` can be active on a [`Connection`](@ref) at once. If multiple `AsyncResult`s use the same `Connection`, they will execute serially but without any guarantee of order.

`async_execute` does not yet support [`Statement`](@ref)s.

`async_execute` optionally takes a `parameters` vector which passes query parameters as strings to PostgreSQL.

`binary_format`, when set to true, will transfer the data in binary format. Support for binary transfer is currently limited to a subset of basic data types.

Queries without parameters can contain multiple SQL statements, and the result of the final statement is returned. Any errors which occur during executed statements will be bundled together in a `CompositeException` and thrown.

As is normal for `Task`s, any exceptions will be thrown when calling `wait` or `fetch`.
