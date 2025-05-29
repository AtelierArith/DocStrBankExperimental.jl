```
Sedol(x::String)
```

セドール識別子を作成します。

# 例

```jldoctest; setup = :(using FinancialSymbology)
julia> sedol_id = Sedol("B0YQ5W0")
"B0YQ5W0"
```
