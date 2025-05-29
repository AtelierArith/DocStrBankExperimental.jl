```
RandomDisk{T<:AbstractFloat} <: Circular{T}
```

Disk-like obstacle that randomly (and uniformly) reflects colliding particles. The propagation is allowed outside of the circle.

### Fields:

  * `c::SVector{2,T}` : Center.
  * `r::T` : Radius.
  * `name::String` : Some name given for user convenience. Defaults to "Random disk".
