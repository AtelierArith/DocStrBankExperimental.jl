```julia
full_hs_matrix(
    M::Array{Array{T<:Number, 2}, 1},
    ed::KeldyshED.EDCore
) -> Matrix{T} where T<:Number

```

Flatten a block-diagonal matrix and return a matrix acting in the full Hilbert space.

## Arguments

  * `M`:  List of matrices' diagonal blocks.
  * `ed`: An Exact Diagonalization object defining the invariant subspace structure.
