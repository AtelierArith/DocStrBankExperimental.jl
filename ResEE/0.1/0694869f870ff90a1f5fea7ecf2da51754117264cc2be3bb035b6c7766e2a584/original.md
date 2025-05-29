```
get_rho!(rho::AbstractMatrix{T}, psi::AbstractVector{T}, M::Union{Matrix{T}, SparseMatrixCSC{T, Int64}}, ij_istate::Vector{Tuple{Int64, Int64}})
```

# Parameters

  * `rho`: dimension dimA × dimA  matrix
  * `M`  : dimension dimA × dimB  matrix (for local constraint, M will NOT be sparse, and regular        Matrix type would be better)
  * `ij_istate` :: istate to intermediate matrix M index (i, j) mapping table

# Example

```juila-repl
julia> rho, res... = get_rho_M_ijmap(state_istate, Float64; S=S, L=L); 
julia> get_rho!(rho, psi, res...)
```
