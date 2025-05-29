```
mass_center(a::Array{T}) where T <: AbstractParticle
mass_center(a::StructArray)
```

Compute mass center of particles, which is weighted by mass.

There are differences among `center`, `pos_center`, `mass_center` and `median`:

  * `center`: box center of particles
  * `pos_center`: average position of particles
  * `mass_center`: mass weighted average position of particles
  * `median`: middle value of positions of particles
