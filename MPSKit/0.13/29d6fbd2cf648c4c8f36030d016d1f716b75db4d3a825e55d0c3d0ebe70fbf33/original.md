```julia
struct RandExpand{S} <: MPSKit.Algorithm
```

An algorithm that expands the bond dimension by adding random unitary vectors that are orthogonal to the existing state. This is achieved by performing a truncated SVD on a random two-site MPS tensor, which is made orthogonal to the existing state.

## Fields

  * `alg_svd::Any`: algorithm used for the singular value decomposition
  * `trscheme::TensorKit.TruncationScheme`: algorithm used for [truncation](@extref TensorKit.tsvd] the expanded space
