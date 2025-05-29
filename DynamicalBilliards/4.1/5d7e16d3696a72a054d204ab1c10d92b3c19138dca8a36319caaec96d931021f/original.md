```
FiniteSplitterWall{T<:AbstractFloat} <: Wall{T}
```

Finite wall obstacle allowing fow ray-splitting (mutable type).

### Fields:

  * `sp::SVector{2,T}` : Starting point of the Wall.
  * `ep::SVector{2,T}` : Ending point of the Wall.
  * `normal::SVector{2,T}` : Normal vector to the wall, pointing to where the particle *will come from before a collision* (pointing towards the inside of the billiard). The size of the vector is irrelevant since it is internally normalized.
  * `isdoor::Bool` : Flag of whether this `FiniteSplitterWall` instance is a "Door". Defaults to `false`.
  * `pflag::Bool` : Flag that keeps track of where the particle is currently propagating (`pflag` = propagation flag). `true` is associated with the `normal` vector the wall is instantiated with. Defaults to `true`.
  * `name::String` : Name of the obstacle, given for user convenience. Defaults to "Finite Splitter Wall".
