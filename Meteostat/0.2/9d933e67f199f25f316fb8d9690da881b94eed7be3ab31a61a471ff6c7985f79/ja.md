```
get_stations(
    point::Point,
    granularity::Type{T},
    start_date::Dates.Date,
    end_date::Dates.Date;
    radius::Union{Float64,Nothing}=35_000.0,
)
```

指定されたポイントの半径距離内にあるすべてのステーションを読み取り、要求された粒度と日付範囲でデータが利用可能な場所を取得します。
