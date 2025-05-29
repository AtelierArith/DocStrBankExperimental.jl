```
get_stations(
    point::Point,
    granularity::Type{T},
    start_date::Dates.Date,
    end_date::Dates.Date;
    radius::Union{Float64,Nothing}=35_000.0,
)
```

Reads all stations within radius distance of the point and where data is available for the requested granularity and date range
