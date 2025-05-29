```
selinv(F::SparseArrays.CHOLMOD.Factor; depermute=false)
    -> @NamedTuple{Z::AbstractMatrix, p::Vector{Int64}}
```

Compute the selected inverse `Z` of some matrix `A` based on its sparse Cholesky factorization `F`.

# Arguments

  * `F::SparseArrays.CHOLMOD.Factor`:       Sparse Cholesky factorization of some matrix `A`.       `F` will be used internally for the computations underlying the       selected inversion of `A`.

# Keyword arguments

  * `depermute::Bool`: Whether to depermute the selected inverse or not.

# Returns

A named tuple `Zp`. `Zp.Z` is the selected inverse, and `Zp.p` is the permutation vector of the corresponding sparse Cholesky factorization.
