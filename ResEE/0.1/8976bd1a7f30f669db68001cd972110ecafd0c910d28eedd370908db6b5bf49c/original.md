```
get_entEntropy!(psi::AbstractVector{T}, rhoList::Vector{Matrix{T}}, MList::Vector{Matrix{T}}, ij_igroup_istate::Vector{Tuple{Int32, Int32, UInt8}})
```

get the entanglement entropy of istate wavefunction `psi` using the block restricted reshape method for U1 conserved system.

# Example

```juila-repl
julia> res... = get_rhos_Ms_ijkmap(state_istate, Float64; S=S, L=L)
julia> entEntropy = get_entEntropy!(psi, res...) 
julia>
julia> rhoList, MList, ij_igroup_istate = get_rhos_Ms_ijkmap(state_istate, Float64; S=S, L=L)
julia> entEntropy = get_entEntropy!(psi, rhoList, MList, ij_igroup_istate) 
```
