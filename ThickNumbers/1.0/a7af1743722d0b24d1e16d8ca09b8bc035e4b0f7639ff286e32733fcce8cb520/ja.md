```
valuetype(::Type{<:ThickNumber})
```

スパン内の数値の型、すなわち `ThickNumber{T}` の `T` を返します。

# 例

```julia
julia> valuetype(Interval{Float64})
Float64
```
