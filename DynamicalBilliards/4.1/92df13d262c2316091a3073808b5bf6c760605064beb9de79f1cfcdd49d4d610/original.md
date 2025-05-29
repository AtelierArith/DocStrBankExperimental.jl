```
visited_obstacles!([p::AbstractParticle,] bd::Billiard, t)
```

Evolve the given particle `p` inside the billiard `bd` exactly like [`evolve!`](@ref). However return only:

  * `ts::Vector{T}` : Vector of time points of when each collision occured.
  * `obst::Vector{Int}` : Vector of obstacle indices in `bd` that the particle collided with at the time points in `ts`.

The first entries are `0.0` and `0`. Similarly with [`evolve!`](@ref) the function does not record collisions with periodic walls.

Currently does not support raysplitting. Returns empty arrays for pinned particles.
