```
indices(ga::GeoArray, p::SVector{2,<:Real}, strategy::AbstractStrategy, rounding::RoundingMode)
```

Retrieve logical indices of the cell represented by coordinates `p`. `strategy` can be used to define whether the coordinates represent the center (`Center`) or the top left corner (`Vertex`) of the cell. `rounding` can be used to define how the coordinates are rounded to the nearest integer index. See `coords` for the inverse function.
