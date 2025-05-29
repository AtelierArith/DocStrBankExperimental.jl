```
get_stations(point::Point, granularity::Type{T}; radius::Union{Float64,Nothing}=35_000.0) where {T<:Dates.Period}
```

Reads all stations within radius distance of the point and where data is available for the requested granularity
