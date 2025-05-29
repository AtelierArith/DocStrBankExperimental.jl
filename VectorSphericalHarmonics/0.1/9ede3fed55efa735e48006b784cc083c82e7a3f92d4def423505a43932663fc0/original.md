```
genspharm(modes::Union{SphericalHarmonicModes.LM, SphericalHarmonicModes.ML}, θ, ϕ, [S = maximum(SphericalHarmonicModes.l_range(modes))])
```

Evaluate the diagonal elements of the Phinney-Burridge ([`PB`](@ref)) vector spherical harmonics in the [`HelicityCovariant`](@ref) basis for all modes `(j,m)` in `modes`.

A pre-allocated array of scalar spherical harmonics `S` may be passed as the final argument. This may be generated using [`VectorSphericalHarmonics.cache`](@ref).
