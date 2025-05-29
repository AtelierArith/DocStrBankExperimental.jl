```
function minimum_y(a::Array{T,N}) where T <: AbstractPoint where N
function minimum_y(a::Array{T,N}) where T <: AbstractParticle where N
function minimum_y(a::StructArray)
```

Return the minimum `:y` field of points in array `a` Return the minimum `Pos.y` of particles in array `a`
