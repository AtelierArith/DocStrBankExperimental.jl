```
Semicircle{T<:AbstractFloat} <: Circular{T}
```

Obstacle that represents half a circle. Propagation is allowed only inside the semicircle.

### Fields:

  * `c::SVector{2,T}` : Center.
  * `r::T` : Radius.
  * `facedir::SVector{2,T}` : Direction where the open face of the Semicircle is facing.
  * `name::String` : Name of the obstacle given for user convenience. Defaults to "Semicircle".
