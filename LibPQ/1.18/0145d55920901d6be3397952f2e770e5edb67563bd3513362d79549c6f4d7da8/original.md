```
execute(
    {jl_conn::Connection, query::AbstractString | stmt::Statement},
    [parameters::Union{AbstractVector, Tuple},]
    throw_error::Bool=true,
    binary_format::Bool=false,
    column_types::AbstractDict=ColumnTypeMap(),
    type_map::AbstractDict=LibPQ.PQTypeMap(),
    conversions::AbstractDict=LibPQ.PQConversions(),
    not_null::Union{Bool, AbstractVector}=false,
) -> Result
```

Run a query on the PostgreSQL database and return a `Result`. If `throw_error` is `true`, throw an error and clear the result if the query results in a fatal error or unreadable response.

The query may be passed as `Connection` and `AbstractString` (SQL) arguments, or as a `Statement`.

`execute` optionally takes a `parameters` vector which passes query parameters as strings to PostgreSQL.

`column_types` accepts type overrides for columns in the result which take priority over those in `type_map`.

`not_null` indicates whether parsed columns should be able to contain null values, parsed as `missing`. The argument can be a single `Bool` for all columns, a list of `Bool`, or a list of column names.

For information on the `column_types`, `type_map`, and `conversions` arguments, see [Type Conversions](@ref typeconv).

`binary_format`, when set to true, will transfer the data in binary format. Support for binary transfer is currently limited to a subset of basic data types.
