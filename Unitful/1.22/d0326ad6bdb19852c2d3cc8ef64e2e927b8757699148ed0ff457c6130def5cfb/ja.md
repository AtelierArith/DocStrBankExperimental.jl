```
unit(x::Dates.FixedPeriod)
unit(x::Type{<:Dates.FixedPeriod})
```

特定の期間に対応する単位を返します。

# 例

```jldoctest
julia> using Dates

julia> unit(Second(15)) == u"s"
true

julia> unit(Hour) == u"hr"
true
```
