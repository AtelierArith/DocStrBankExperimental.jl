```
get_stations(point::Point, granularity::Type{T}; radius::Union{Float64,Nothing}=35_000.0) where {T<:Dates.Period}
```

指定された粒度のデータが利用可能な範囲内で、ポイントから半径距離内のすべての駅を読み取ります。
