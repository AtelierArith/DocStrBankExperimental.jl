```julia
mutable struct FBDMD{R} <: DataDrivenDMD.AbstractKoopmanAlgorithm
```

Approximates the Koopman operator `K` via the forward-backward DMD. It is assumed that `K = sqrt(K₁*inv(K₂))`, where `K₁` is the approximation via forward and `K₂` via [DMDSVD](@ref). Based on [this paper](https://arxiv.org/pdf/1507.02264.pdf).

If `truncation` ∈ (0, 1) is given, the singular value decomposition is reduced to include only entries bigger than `truncation*maximum(Σ)`. If `truncation` is an integer, the reduced SVD up to `truncation` is used for computation.

# Fields

  * `alg`

# Signatures
