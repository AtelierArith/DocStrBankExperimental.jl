```
fetch_data(point::Point, granularity::Type{T};
    year::Union{Int, Nothing} = nothing,
    ) where {T <: Dates.Period}
```

Fetches weather data for a given point and requested granularity
