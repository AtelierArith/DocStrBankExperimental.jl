```
vshbasis(Y::AbstractVSH, B::Basis, j::Integer, m::Integer, n::Integer, θ, ϕ, [S = VectorSphericalHarmonics.cache(θ, ϕ, j)])
```

Evaluate the components of the vector spherical harmonics $\mathbf{Y}_{j m}^n(θ, ϕ)$ in the basis `B`. A pre-allocated array of scalar spherical harmonics `S` may be passed as the final argument. This may be generated using [`VectorSphericalHarmonics.cache`](@ref).
