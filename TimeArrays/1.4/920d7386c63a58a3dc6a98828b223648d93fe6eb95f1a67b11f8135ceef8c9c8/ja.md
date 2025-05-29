```
TimeTick{T,V}(x::Tuple{TimeLike,Any})
TimeTick(x::Tuple{T,V})
```

タプル `x` から [`TimeTick`](@ref) オブジェクトを構築します。このタプルにはタイムスタンプと値が含まれています。

## 例

```jldoctest
julia> using Dates

julia> TimeTick{Date,Float64}((DateTime("2024-01-01T00:00:00"), 100))
TimeTick(2024-01-01, 100.0)

julia> TimeTick((DateTime("2024-01-01T00:00:00"), 100))
TimeTick(2024-01-01T00:00:00, 100)
```
