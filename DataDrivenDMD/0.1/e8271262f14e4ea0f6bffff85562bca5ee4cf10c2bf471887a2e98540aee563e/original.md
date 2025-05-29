```julia
mutable struct DMDPINV <: DataDrivenDMD.AbstractKoopmanAlgorithm
```

Approximates the Koopman operator `K` based on

```julia
K = Y / X
```

where `Y` and `X` are data matrices. Returns a  `Eigen` factorization of the operator.

# Fields

# Signatures
