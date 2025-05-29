```
TimeTick{T,V}(timestamp::TimeLike, value)
TimeTick(timestamp::T, value::V)
```

渡された `timestamp` と `value` で [`TimeTick`](@ref) オブジェクトを構築します。

## 例

```jldoctest
julia> using Dates

julia> TimeTick{Date,Float64}(DateTime("2024-01-01T00:00:00"), 100)
TimeTick(2024-01-01, 100.0)

julia> TimeTick(DateTime("2024-01-01T00:00:00"), 100)
TimeTick(2024-01-01T00:00:00, 100)
```
