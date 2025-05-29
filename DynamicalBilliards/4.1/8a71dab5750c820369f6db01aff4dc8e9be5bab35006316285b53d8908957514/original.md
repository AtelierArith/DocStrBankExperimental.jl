```
Disk{T<:AbstractFloat}  <: Circular{T}
```

Disk-like obstacle with propagation allowed outside of the circle (immutable type).

### Fields:

  * `c::SVector{2,T}` : Center.
  * `r::T` : Radius.
  * `name::String` : Some name given for user convenience. Defaults to "Disk".
