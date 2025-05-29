```julia
struct SvdCut{S} <: MPSKit.Algorithm
```

An algorithm that uses truncated SVD to change the bond dimension of a ψ.

## Fields

  * `alg_svd::Any`: algorithm used for the singular value decomposition
  * `trscheme::TensorKit.TruncationScheme`: algorithm used for [truncation][@extref TensorKit.tsvd] of the gauge tensors
