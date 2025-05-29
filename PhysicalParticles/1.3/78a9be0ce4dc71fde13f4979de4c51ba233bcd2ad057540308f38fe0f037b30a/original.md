```julia
center(
    a::Array{T<:Union{PhysicalParticles.AbstractParticle2D, PhysicalParticles.AbstractPoint2D}, N}
) -> Any

```

Compute box center of points or particles

There are differences among `center`, `pos_center`, `mass_center` and `median`:

  * `center`: box center of particles
  * `pos_center`: average position of particles
  * `mass_center`: mass weighted average position of particles
  * `median`: middle value of positions of particles
