```
fetch_data(
    point::Point, start_date::Dates.Date, end_date::Dates.Date, granularity::Type{T},
    year::Union{Int, Nothing} = nothing) where {T <: Dates.Period}
```

Fetches hourly weather data for a given date range
