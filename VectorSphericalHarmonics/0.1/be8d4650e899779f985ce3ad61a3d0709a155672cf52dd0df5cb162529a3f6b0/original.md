```
genspharm(j, m, θ, ϕ, [S = VectorSphericalHarmonics.cache(θ, ϕ, j)])
```

Evaluate the diagonal elements of the Phinney-Burridge ([`PB`](@ref)) vector spherical harmonics in the [`HelicityCovariant`](@ref) basis for one mode `(j,m)`. Returns an array `Y` whose elements `Y[n]` are given by

$$
Y_{jm}^N(\theta,\phi) = \left[\mathbf{P}_{j m}^N(θ, ϕ)\right]^N
$$

These components are referred to as "generalized spherical harmonics" by Dahlen & Tromp (1998), which is the nomenclature used here.

A pre-allocated array of scalar spherical harmonics `S` may be passed as the final argument. This may be generated using [`VectorSphericalHarmonics.cache`](@ref).
