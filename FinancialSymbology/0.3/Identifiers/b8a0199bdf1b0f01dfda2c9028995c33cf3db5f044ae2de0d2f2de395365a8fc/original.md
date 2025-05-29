```
Sedol(x::String)
```

Create a Sedol Identifier.

# Example

```jldoctest; setup = :(using FinancialSymbology)
julia> sedol_id = Sedol("B0YQ5W0")
"B0YQ5W0"
```
