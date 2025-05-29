```
function minimum_z(a::Array{T,N}) where T <: AbstractPoint where N
function minimum_z(a::Array{T,N}) where T <: AbstractParticle where N
function minimum_z(a::StructArray)
```

Return the minimum `:z` field of points in array `a` Return the minimum `Pos.z` of particles in array `a`
