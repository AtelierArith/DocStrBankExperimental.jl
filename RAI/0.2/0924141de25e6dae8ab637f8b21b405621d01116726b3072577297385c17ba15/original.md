```
exec(ctx, "database", "engine", "query source"; kwargs...)
```

Synchronously execute a provided query string in the supplied database. This function creates a Transaction using the supplied engine, and then polls the Transaction until it has completed, and returns a Dict holding the Transaction resource and its results and metadata.

## Keyword Arguments:

  * `readonly = false`: If true, this is a "read-only query", and the effects of this  transaction will not be committed to the database.
  * `inputs`: Optional dictionary of input pairs, mapping a relation name to a value.  (Deprecated - the format of the inputs Dict will change in upcoming releases.)

# Examples:

```julia
julia> exec(ctx, "my_database", "my_engine", "def output {2 + 2}")
Dict{String, Any} with 4 entries:
  "metadata"    => Union{}[]
  "problems"    => Union{}[]
  "results"     => Pair{String, Arrow.Table}["/:output/Int64"=>Arrow.Table with 1 r…
  "transaction" => {…

julia> exec(ctx, "my_database", "my_engine", """
           def insert[:my_relation]: (1, 2, 3)
           """,
           readonly = false,
       )
Dict{String, Any} with 4 entries:
  "metadata"    => Union{}[]
  "problems"    => Union{}[]
  "results"     => Any[]
  "transaction" => {…
```
