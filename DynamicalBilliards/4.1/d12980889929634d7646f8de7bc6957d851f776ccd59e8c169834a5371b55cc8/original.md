```
PeriodicWall{T<:AbstractFloat} <: Wall{T}
```

Wall obstacle that imposes periodic boundary conditions upon collision (immutable type).

### Fields:

  * `sp::SVector{2,T}` : Starting point of the Wall.
  * `ep::SVector{2,T}` : Ending point of the Wall.
  * `normal::SVector{2,T}` : Normal vector to the wall, pointing to where the particle *will come from* (to the inside the billiard). The size of the vector is **important**! This vector is added to a particle's `pos` during collision. Therefore the size of the normal vector must be correctly associated with the size of the periodic cell.
  * `name::String` : Name of the obstacle, given for user convenience. Defaults to "Periodic wall".
