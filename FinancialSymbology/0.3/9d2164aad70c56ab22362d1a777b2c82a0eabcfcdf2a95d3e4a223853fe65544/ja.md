```
makeidentifier(x::String)
```

自動的に [`Identifier`](@ref identifier_header) を検出し、適切な `Type` を作成します。

参照: [`fetchsecuritydata`](@ref)

# 例

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
