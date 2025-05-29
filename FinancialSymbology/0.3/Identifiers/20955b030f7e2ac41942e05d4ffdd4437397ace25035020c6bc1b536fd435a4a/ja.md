```
Cusip(x::String)
```

CUSIP識別子を作成します。

# 例

```jldoctest; setup = :(using FinancialSymbology)
julia> cusip_id = Cusip("037833100")
"037833100"
```
