```
function minimum_x(a::Array{T,N}) where T <: AbstractPoint where N
function minimum_x(a::Array{T,N}) where T <: AbstractParticle where N
function minimum_x(a::StructArray)
```

Return the minimum `:x` field of points in array `a` Return the minimum `Pos.x` of particles in array `a`
