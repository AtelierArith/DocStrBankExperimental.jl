```
transmission(flm::Film, xrayE::AbstractFloat, θ::AbstractFloat = π/2, alg::Type{<:NeXLAlgorithm} = DefaultAlgorithm)
transmission(flm::Film, cxr::CharXRay, θ::AbstractFloat = π/2, alg::Type{<:NeXLAlgorithm} = DefaultAlgorithm)
```

Compute the transmission fraction of an X-ray at the specified angle through a Film.
