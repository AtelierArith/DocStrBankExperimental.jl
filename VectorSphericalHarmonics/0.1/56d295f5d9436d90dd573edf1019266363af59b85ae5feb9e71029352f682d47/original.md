```
vshbasis(Y::AbstractVSH, B::Basis, modes::Union{SphericalHarmonicModes.LM, SphericalHarmonicModes.ML}, θ, ϕ, [S = maximum(SphericalHarmonicModes.l_range(modes))])
```

Evaluate a set of vector spherical harmonics $\mathbf{Y}_{j m}^\alpha(θ, ϕ)$ for valid values of $\alpha$ for all `(j,m)` in `modes`, and return their components in the basis `B`. A pre-allocated array of scalar spherical harmonics `S` may be passed as the final argument. This may be generated using [`VectorSphericalHarmonics.cache`](@ref).
