```
lyapunovspectrum([p::AbstractParticle,] bd::Billiard, t)
```

Returns the finite time lyapunov exponents (averaged over time `t`) for a given particle in a billiard table using the method outlined in [1]. `t` can be either `Float` or `Int`, meaning total time or total amount of collisions.

Returns zeros for pinned particles.

If a particle is not given, a random one is picked through [`randominside`](@ref). See [`parallelize`](@ref) for a parallelized version.

[1] : Ch. Dellago *et al*, [Phys. Rev. E **53** (1996)](http://link.aps.org/doi/10.1103/PhysRevE.53.1485)
