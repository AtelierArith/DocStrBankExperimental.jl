```
block_tridgm(main_diag::Vector{Matrix{T}}, upper_diag::Vector{Matrix{T}}, lower_diag::Vector{Matrix{T}}) where {T<:Real}
```

Construct a block tridiagonal matrix from three vectors of matrices.

# Arguments

  * `main_diag::Vector{Matrix{T}}`: Vector of matrices for the main diagonal.
  * `upper_diag::Vector{Matrix{T}}`: Vector of matrices for the upper diagonal.
  * `lower_diag::Vector{Matrix{T}}`: Vector of matrices for the lower diagonal.

# Returns

  * A sparse matrix representing the block tridiagonal matrix.

# Throws

  * `ErrorException` if the lengths of `upper_diag` and `lower_diag` are not one less than the length of `main_diag`.
