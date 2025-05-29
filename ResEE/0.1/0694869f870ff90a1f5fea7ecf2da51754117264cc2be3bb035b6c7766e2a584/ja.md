```
get_rho!(rho::AbstractMatrix{T}, psi::AbstractVector{T}, M::Union{Matrix{T}, SparseMatrixCSC{T, Int64}}, ij_istate::Vector{Tuple{Int64, Int64}})
```

# パラメータ

  * `rho`: 次元 dimA × dimA の行列
  * `M`  : 次元 dimA × dimB の行列（ローカル制約の場合、M はスパースではなく、通常の行列タイプが望ましい）
  * `ij_istate` :: 中間行列 M のインデックス (i, j) マッピングテーブルへの istate

# 例

```juila-repl
julia> rho, res... = get_rho_M_ijmap(state_istate, Float64; S=S, L=L); 
julia> get_rho!(rho, psi, res...)
```
