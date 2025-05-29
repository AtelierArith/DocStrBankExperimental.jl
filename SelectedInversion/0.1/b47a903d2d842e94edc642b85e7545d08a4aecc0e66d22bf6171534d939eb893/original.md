```
selinv(A::SparseMatrixCSC; depermute=false)
    -> @NamedTuple{Z::AbstractMatrix, p::Vector{Int64}}
```

Compute the selected inverse `Z` of `A`. The sparsity pattern of `Z` corresponds to that of the Cholesky factor of `A`, and the nonzero entries of `Z` match the corresponding entries in `A⁻¹`.

# Arguments

  * `A::SparseMatrixCSC`: The sparse symmetric positive definite matrix for which                       the selected inverse will be computed.

# Keyword arguments

  * `depermute::Bool`: Whether to depermute the selected inverse or not.

# Returns

A named tuple `Zp`. `Zp.Z` is the selected inverse, and `Zp.p` is the permutation vector of the corresponding sparse Cholesky factorization.
