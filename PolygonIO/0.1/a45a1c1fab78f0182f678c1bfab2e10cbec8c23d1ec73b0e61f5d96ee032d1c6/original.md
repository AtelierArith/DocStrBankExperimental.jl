```
PolyOpts <: AbstractPolyOptions
```

User options for the PolygonIO.

# Options

  * api_key: String representing the API key from a registered polygon.io account.
  * table: Whether to covnert extracted results as a table or not. Compatible Table.jl or nothing for raw JSONs.

# Examples

```julia-repl
julia> using PolygonIO, DataFrames
julia> opts = PolyOpts(API_KEY, DataFrame)  # if user wants tabularised output
julia> opts = PolyOpts(API_KEY, nothing)    # if user wants raw JSON output
```
