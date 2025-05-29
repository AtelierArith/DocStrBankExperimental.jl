```
phantom(x::Vector, y::Vector, oa::Array{<:Object2d}, oversample::Int; T)
```

Return a 2D digital image of the phantom sampled at grid of `(x,y)` locations, with over-sampling factor `oversample` and element type `T`.
