```julia
struct ExactScatteringKernel{T, S, N} <: ScatteringOptics.AbstractScatteringKernel{T}
```

A Comrade VLBI Sky Model for the scattering kernel based on a Scattering Model `sm <: AbstractScatteringModel` using the exact formula in Psaltis et al. (2018).

By default if `T` isn't given, `T` defaults to `Float64`
