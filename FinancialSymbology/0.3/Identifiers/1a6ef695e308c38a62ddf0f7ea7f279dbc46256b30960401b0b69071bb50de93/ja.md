```
Isin(x::String)
```

ISIN識別子を作成します。

# 例

```jldoctest; setup = :(using FinancialSymbology)
julia> isin_id = Isin("US0378331005")
"US0378331005"
```
