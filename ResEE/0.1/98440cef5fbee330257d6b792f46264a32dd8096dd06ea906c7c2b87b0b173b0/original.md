```
get_rho(psi::AbstractVector{T}, MList::Vector{Matrix{T}}, ij_igroup_istate::Vector{Tuple{Int32, Int32, UInt8}})
```

in place create the block diagonal sparse reduced density matrix rho leveraging the U1 conservation.

# Example

```juila-repl
julia> _, res... = get_rhos_Ms_ijkmap(state_istate, Float64; S=S, L=L)
julia> rho = get_rho(psi, res...) 
julia>
julia> rhoList, MList, ij_igroup_istate = get_rhos_Ms_ijkmap(state_istate, Float64; S=S, L=L)
julia> rho = get_rho(psi, MList, ij_igroup_istate) 
```
