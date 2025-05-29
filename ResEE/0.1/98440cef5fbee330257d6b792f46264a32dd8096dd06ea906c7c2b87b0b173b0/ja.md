```
get_rho(psi::AbstractVector{T}, MList::Vector{Matrix{T}}, ij_igroup_istate::Vector{Tuple{Int32, Int32, UInt8}})
```

U1保存則を利用してブロック対角スパース縮約密度行列rhoをインプレースで作成します。

# 例

```juila-repl
julia> _, res... = get_rhos_Ms_ijkmap(state_istate, Float64; S=S, L=L)
julia> rho = get_rho(psi, res...) 
julia>
julia> rhoList, MList, ij_igroup_istate = get_rhos_Ms_ijkmap(state_istate, Float64; S=S, L=L)
julia> rho = get_rho(psi, MList, ij_igroup_istate) 
```
