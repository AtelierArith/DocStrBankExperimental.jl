```
coords(ga::GeoArray, p::SVector{2,<:Integer}, strategy::AbstractStrategy=Center())
coords(ga::GeoArray, p::Tuple{<:Integer,<:Integer}, strategy::AbstractStrategy=Center())
coords(ga::GeoArray, p::CartesianIndex{2}, strategy::AbstractStrategy=Center())
```

Retrieve coordinates of the cell index by `p`. See `indices` for the inverse function.
