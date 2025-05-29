```
function filter_inventory!(
    stations, granularity::Type{T}, period::Tuple{Dates.Date,Dates.Date}
)
```

Filter weather stations by inventory data between two dates (pass `nothing` for normals)
