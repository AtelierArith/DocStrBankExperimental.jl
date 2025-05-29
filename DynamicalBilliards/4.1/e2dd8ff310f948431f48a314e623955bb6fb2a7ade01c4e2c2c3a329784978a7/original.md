```
phasespace_portion(bd::Billiard, t, p::AbstractParticle, δξ, δφ = δξ)
```

Calculate the portion of the phase space of the billiard `bd` covered by the particle `p` when it is evolved for time `t` (float or integer).

This function extends [`boundarymap_portion`](@ref) using a novel approach. For each visited box of the boundary map, [`bounce!`](@ref) attributes a third dimension (the collision time, equal to collision distance) which expands the two dimensions of the boundary map to the three dimensions of the phase space.

The true phase space portion is then the weighted portion of boxes visited by the particle, divided by the total weighted sum of boxes. The weights of the boxes are the collision times.
