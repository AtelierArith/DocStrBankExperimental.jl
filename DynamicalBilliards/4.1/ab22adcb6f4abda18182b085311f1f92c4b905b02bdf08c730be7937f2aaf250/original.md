```
boundarymap_portion(bd::Billiard, t, p::AbstractParticle, δξ, δφ = δξ)
```

Calculate the portion of the boundary map of the billiard `bd` covered by the particle `p` when it is evolved for time `t` (float or integer). Notice that the

The boundary map is partitioned into boxes of size `(δξ, δφ)` and as the particle evolves visited boxes are counted. The returned ratio is this count divided by the total boxes of size `(δξ, δφ)` needed to cover the boundary map.

**Important:** This portion **does not** equate the portion the particle's orbit covers on the full, three dimensional phase space. Use the function [`phasespace_portion`](@ref) for that!
