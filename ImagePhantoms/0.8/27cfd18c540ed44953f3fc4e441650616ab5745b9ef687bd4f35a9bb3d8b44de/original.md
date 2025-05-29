```
phantom(x::Vector, y::Vector, oa::Array{<:Object2d})
```

Return a 2D digital image of the phantom sampled at grid of `(x,y)` locations. Returned 2D image size is `length(x) × length(y)`.
