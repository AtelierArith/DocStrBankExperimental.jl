```julia
struct ApproximatedScatteringKernel{T, S, N} <: ScatteringOptics.AbstractScatteringKernel{T}
```

A Comrade VLBI Sky Model for the scattering kernel based on a Scattering Model `sm <: AbstractScatteringModel` using the fast approximation formula in Psaltis et al. (2018).

If `T` isn't given, `T` defaults to `Float64`
