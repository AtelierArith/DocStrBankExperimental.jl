```
get_rho(psi::AbstractVector{T}, M::Union{Matrix{T}, SparseMatrixCSC{T, Int64}}, ij_istate::Vector{Tuple{Int32, Int32}})
```

return the density matrix rho using the restricted reshape method.

# Example

```juila-repl
julia> rho, res... = get_rho_M_ijmap(state_istate, Float64; S=S, L=L); 
julia> rho = get_rho(psi, res...) 
```
