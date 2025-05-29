```
function maximum_x(a::Array{T,N}) where T <: AbstractPoint where N
function maximum_x(a::Array{T,N}) where T <: AbstractParticle where N
function maximum_x(a::StructArray)
```

Return the maximum `:x` field of points in array `a` Return the maximum `Pos.x` of particles in array `a`
