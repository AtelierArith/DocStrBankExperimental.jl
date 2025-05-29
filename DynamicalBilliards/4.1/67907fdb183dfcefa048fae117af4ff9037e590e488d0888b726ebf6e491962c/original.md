```
FiniteWall{T<:AbstractFloat} <: Wall{T}
```

Wall obstacle imposing specular reflection during collision (immutable type). Slower than [`InfiniteWall`](@ref), meant to be used for non-convex billiards.

Giving a `true` value to the field `isdoor` designates this obstacle to be a `Door`. This is used in [`escapetime`](@ref) function. A `Door` is a obstacle of the billiard that the particle can escape from, thus enabling calculations of escape times.

### Fields:

  * `sp::SVector{2,T}` : Starting point of the Wall.
  * `ep::SVector{2,T}` : Ending point of the Wall.
  * `normal::SVector{2,T}` : Normal vector to the wall, pointing to where the particle *will come from before a collision* (pointing towards the inside of the billiard). The size of the vector is irrelevant since it is internally normalized.
  * `isdoor::Bool` : Flag of whether this `FiniteWall` instance is a "Door". Defaults to `false`.
  * `name::String` : Name of the obstacle, given for user convenience. Defaults to "Finite Wall".
