```
struct Particles{T, N} <: AbstractParticles{T, N}
```

This type represents uncertainty using a cloud of particles.

# Constructors:

  * `Particles()`
  * `Particles(N::Integer)`
  * `Particles([rng::AbstractRNG,] d::Distribution)`
  * `Particles([rng::AbstractRNG,] N::Integer, d::Distribution; permute=true, systematic=true)`
  * `Particles(v::Vector{T} where T)`
  * `Particles(m::Matrix{T} where T)`: Creates multivariate particles (Vector{Particles})
