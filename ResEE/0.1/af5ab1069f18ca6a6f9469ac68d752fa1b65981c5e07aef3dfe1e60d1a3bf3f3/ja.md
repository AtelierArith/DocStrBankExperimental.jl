```
get_rhos_Ms_ijkmap(state_istate::Vector{Int}, T::Type=ComplexF64; S::Real, L::Int, LA::Int=0)
```

ブロック制限されたリシェイプマップ `istate -> (i, j, iblock)`、ブロック密度行列 `rho` および U1 保存を使用した補助ブロック `M` を返します。

# 例

```julia-repl
julia> rhoList, MList, ij_igroup_istate = get_rhos_Ms_ijkmap(state_istate, Float64; S=S, L=L)
```
