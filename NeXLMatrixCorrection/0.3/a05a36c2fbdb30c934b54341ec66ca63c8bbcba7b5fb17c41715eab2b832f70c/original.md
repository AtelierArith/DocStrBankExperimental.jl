```
kcoating(ty::Type{<:MatrixCorrection}, subtrate::Material, coating::Material, cxr::CharXRay, e0::AbstractFloat, toa::AbstractFloat, τ::AbstractFloat)
```

Estimate the k-ratio for a coating of mass-thickness τ (g/cm²) on the specified substrate. The standard for the coating is assumed to be of the same material as the coating.
