```
makeidentifier(x::String)
```

Automatically detect [`Identifier`](@ref identifier_header) and create appropriate `Type`.

See also: [`fetchsecuritydata`](@ref)

# Example

```jldoctest; setup = :(using FinancialSymbology)
julia> ids = makeidentifier.(["AAPL US Equity", "BDDXSM4"])
2-element Vector{Identifier}:
 "AAPL US Equity"
 "BDDXSM4"

julia> typeof.(ids)
2-element Vector{DataType}:
 Ticker
 Sedol
```
