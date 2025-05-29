```
RandomWall{T<:AbstractFloat} <: Wall{T}
```

Wall obstacle imposing (uniformly) random reflection during collision (immutable type).

### Fields:

  * `sp::SVector{2,T}` : Starting point of the Wall.
  * `ep::SVector{2,T}` : Ending point of the Wall.
  * `normal::SVector{2,T}` : Normal vector to the wall, pointing to where the particle *is expected to come from* (pointing towards the inside of the billiard).
  * `name::String` : Name of the obstacle, given for user convenience. Defaults to "Random wall".
