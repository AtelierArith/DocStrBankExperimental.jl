```julia
struct TBlob{T} <: VLBISkyModels.GeometricModel{T}
```

Constructs a model whose intensity profile is the two dimensional T distriburtion with degrees of freedom `s`. The normalization is such that the flux is unity.

The intensity profile is given by

I(r) = Γ((s+2)/2) / (Γ(s/2) * s * π) * (1 + r²/s)^(-(s+2)/2)

where `r` is the radius from the center of the blob. As s → ∞ this approaches the unit Gaussian.
