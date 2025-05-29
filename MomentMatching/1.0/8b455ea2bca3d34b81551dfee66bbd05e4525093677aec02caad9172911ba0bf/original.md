```julia
mdiff(
    mode::MomentMatching.EstimationMode,
    m::AbstractVector,
    momdat::AbstractVector,
    mmomdat::AbstractVector
) -> Any

```

Computes deviation of model moments from data moments. Should be defined for any subtype of [`EstimationMode`](@ref).

Default: deviation is obtained by rescaling differences with data means of respective quantities.
