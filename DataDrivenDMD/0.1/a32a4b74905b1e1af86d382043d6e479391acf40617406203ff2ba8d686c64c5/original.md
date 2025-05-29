```julia
mutable struct TOTALDMD{R, A} <: DataDrivenDMD.AbstractKoopmanAlgorithm
```

Approximates the Koopman operator `K` with the algorithm `alg` over the rank-reduced data matrices `Xᵣ = X Qᵣ` and `Yᵣ = Y Qᵣ`, where `Qᵣ` originates from the singular value decomposition of the joint data `Z = [X; Y]`. Based on [this paper](http://cwrowley.princeton.edu/papers/Hemati-2017a.pdf).

If `rtol` ∈ (0, 1) is given, the singular value decomposition is reduced to include only entries bigger than `rtol*maximum(Σ)`. If `rtol` is an integer, the reduced SVD up to `rtol` is used for computation.

# Fields

  * `truncation`
  * `alg`

# Signatures
