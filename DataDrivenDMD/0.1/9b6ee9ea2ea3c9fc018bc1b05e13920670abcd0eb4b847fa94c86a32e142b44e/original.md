```julia
mutable struct DMDSVD{T} <: DataDrivenDMD.AbstractKoopmanAlgorithm
```

Approximates the Koopman operator `K` based on the singular value decomposition of `X` such that:

```julia
K = Y*V*Σ*U'
```

where `Y` and `X = U*Σ*V'` are data matrices. The singular value decomposition is truncated via the `truncation` parameter, which can either be an `Int` indicating an index-based truncation or a `Real` indicating a tolerance-based truncation. Returns a `Eigen` factorization of the operator.

# Fields

  * `truncation`: Indicates the truncation

# Signatures
