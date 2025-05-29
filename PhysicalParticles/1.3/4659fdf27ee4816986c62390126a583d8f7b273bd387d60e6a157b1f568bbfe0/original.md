```
function maximum_z(a::Array{T,N}) where T <: AbstractPoint where N
function maximum_z(a::Array{T,N}) where T <: AbstractParticle where N
function maximum_z(a::StructArray)
```

Return the maximum `:z` field of points in array `a` Return the maximum `Pos.z` of particles in array `a`
