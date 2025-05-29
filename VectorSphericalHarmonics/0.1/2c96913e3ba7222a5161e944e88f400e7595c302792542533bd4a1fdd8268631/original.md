```
vshbasis(Y::AbstractVSH, B::Basis, j::Integer, m::Integer, θ, ϕ, [S = VectorSphericalHarmonics.cache(θ, ϕ, j)])
```

Evaluate a set of vector spherical harmonics $\mathbf{Y}_{j m}^\alpha(θ, ϕ)$ for valid values of $\alpha$, and return their components in the basis `B`. A pre-allocated array of scalar spherical harmonics `S` may be passed as the final argument. This may be generated using [`VectorSphericalHarmonics.cache`](@ref).
