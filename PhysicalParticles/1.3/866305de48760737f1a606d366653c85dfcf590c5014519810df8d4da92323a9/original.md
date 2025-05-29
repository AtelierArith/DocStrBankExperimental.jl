```
function median(a::Array{T}, symbol::Symbol) where T <: AbstractParticle
function median(d::Dict, symbol::Symbol)
```

Return the midian value of field `symbol` in array of particles or dict of arrays of particles.

There are differences among `center`, `pos_center`, `mass_center` and `median`:

  * `center`: box center of particles
  * `pos_center`: average position of particles
  * `mass_center`: mass weighted average position of particles
  * `median`: middle value of positions of particles
