```
fetch_data(
    point::Point, start_date::Dates.Date, end_date::Dates.Date, granularity::Type{T},
    year::Union{Int, Nothing} = nothing) where {T <: Dates.Period}
```

指定された日付範囲の時間ごとの天気データを取得します。
