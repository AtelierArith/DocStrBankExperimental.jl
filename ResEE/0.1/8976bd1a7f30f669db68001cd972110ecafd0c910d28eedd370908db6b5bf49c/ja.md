```
get_entEntropy!(psi::AbstractVector{T}, rhoList::Vector{Matrix{T}}, MList::Vector{Matrix{T}}, ij_igroup_istate::Vector{Tuple{Int32, Int32, UInt8}})
```

波動関数 `psi` のエンタングルメントエントロピーを、U1保存系のためのブロック制限リシェイプ法を使用して取得します。

# 例

```juila-repl
julia> res... = get_rhos_Ms_ijkmap(state_istate, Float64; S=S, L=L)
julia> entEntropy = get_entEntropy!(psi, res...) 
julia>
julia> rhoList, MList, ij_igroup_istate = get_rhos_Ms_ijkmap(state_istate, Float64; S=S, L=L)
julia> entEntropy = get_entEntropy!(psi, rhoList, MList, ij_igroup_istate) 
```
