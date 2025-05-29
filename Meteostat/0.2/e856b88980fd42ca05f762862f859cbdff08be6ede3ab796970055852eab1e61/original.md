```
filter_inventory!(stations, granularity::Type{T}) where {T<:Union{Dates.Period,Nothing}}
```

Filter weather stations by inventory data (pass `nothing` for normals)
