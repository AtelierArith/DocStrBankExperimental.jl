```
phantom(x::Vector, y::Vector, z::Vector, oa::Array{<:Object3d})
```

Return a 3D digital image of the phantom sampled at grid of `(x,y,z)` locations. Returned 3D image size is `length(x) × length(y) × length(z)`.
