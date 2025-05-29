```
get_rho_M_ijmap(state_istate::Vector{Int}; S::Real, L::Int, LA::Int=0)
```

制約されたシステムの中間行列インデックス (i, j) マッピングを返します。

# 例

```julia-repl
julia> rho, M, ij_istate = get_rho_M_ijmap(state_istate, Float64; S=S, L=L)
```
