```
addparticles!(sim; centerpos::Vector{SVector}, kwargs...)
```

Like [`addparticle!`](@ref), but for multiple particles (hence the name).

Creates as many particles as `centerpos`es are specified. For vector kwargs, the `i`th entries is used for constructing the `i`th particle. All other kwargs are used for all particles.

## Extended help

### Usage example

```julia
addparticles(sim, centerpos = [SA[0.0, 0.0], SA[1.0, 1.0]], foo = [0.4, -4.5], bar = 5.0, baz = (1.0, 2.0))
```

creates two particles, one at `[0.0, 0.0]`, with `foo = 0.4`, `bar = 5.0` and `baz = (1.0, 2.0)`, and the other at `[1.0, 1.0]`, with `foo = -4.5`, `bar = 5.0` and `baz = (1.0, 2.0)`.
