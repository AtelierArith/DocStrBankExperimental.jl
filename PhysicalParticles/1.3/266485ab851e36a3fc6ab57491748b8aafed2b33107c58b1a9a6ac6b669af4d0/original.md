```
pos_center(a::Array{T}) where T <: AbstractParticle
pos_center(a::StructArray)
```

Compute averaged position with equal weights.  It is different from `middle(a, :Pos)` which computes the middle value of a symbol (useful to avoid influences from distant particles).

There are differences among `center`, `pos_center`, `mass_center` and `median`:

  * `center`: box center of particles
  * `pos_center`: average position of particles
  * `mass_center`: mass weighted average position of particles
  * `median`: middle value of positions of particles
