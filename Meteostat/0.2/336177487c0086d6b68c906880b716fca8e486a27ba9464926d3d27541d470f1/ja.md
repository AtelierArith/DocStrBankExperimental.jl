```
fetch_data(point::Point, granularity::Type{T};
    year::Union{Int, Nothing} = nothing,
    ) where {T <: Dates.Period}
```

指定された地点と要求された粒度の気象データを取得します。
