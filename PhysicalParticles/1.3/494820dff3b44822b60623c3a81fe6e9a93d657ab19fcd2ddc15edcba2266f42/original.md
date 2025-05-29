```
function maximum_y(a::Array{T,N}) where T <: AbstractPoint where N
function maximum_y(a::Array{T,N}) where T <: AbstractParticle where N
function maximum_y(a::StructArray)
```

Return the maximum `:y` field of points in array `a` Return the maximum `Pos.y` of particles in array `a`
