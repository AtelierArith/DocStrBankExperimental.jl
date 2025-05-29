```
struct OrbitStateVector{Tepoch<:Number, T<:Number} <: Orbit{Tepoch, T}
```

Store the state vector representation of an orbit.

# Fields

  * `t::Tepoch`: Epoch [Julian Day].
  * `r::SVector{3, T}`: Position vector [m].
  * `v::SVector{3, T}`: Velocity vector [m/s].
  * `a::SVector{3, T}`: Acceleration vector [m/s²].
