```
InfiniteWall{T<:AbstractFloat} <: Wall{T}
```

Wall obstacle imposing specular reflection during collision (immutable type). Faster than [`FiniteWall`](@ref), meant to be used for convex billiards.

### Fields:

  * `sp::SVector{2,T}` : Starting point of the Wall.
  * `ep::SVector{2,T}` : Ending point of the Wall.
  * `normal::SVector{2,T}` : Normal vector to the wall, pointing to where the particle *will come from before a collision* (pointing towards the inside of the billiard). The size of the vector is irrelevant since it is internally normalized.
  * `name::String` : Name of the obstacle, given for user convenience. Defaults to "Wall".
