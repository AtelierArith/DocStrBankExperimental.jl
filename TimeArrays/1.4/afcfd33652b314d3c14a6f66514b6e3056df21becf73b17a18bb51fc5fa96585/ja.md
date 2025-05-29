```
TimeTick{T,V}(x::NamedTuple{_,Tuple{TimeLike,Any}})
TimeTick(x::NamedTuple{_,Tuple{TimeLike,Any}})
```

名前付きタプル `x` からタイムスタンプと値を含む [`TimeTick`](@ref) オブジェクトを構築します。

## 例

```jldoctest
julia> using Dates

julia> TimeTick{Date,Float64}((timestamp = DateTime("2024-01-01T00:00:00"), value = 100))
TimeTick(2024-01-01, 100.0)

julia> TimeTick((timestamp = DateTime("2024-01-01T00:00:00"), value = 100))
TimeTick(2024-01-01T00:00:00, 100)
```
