```
FuzzyCMeansResult{T<:AbstractFloat}
```

[`fuzzy_cmeans`](@ref) 関数の出力。

# フィールド

  * `centers::Matrix{T}`: 結果のファジークラスタの中心を列として持つ $d×C$ 行列
  * `weights::Matrix{Float64}`: 割り当て重みの $n×C$ 行列 ($\mathrm{weights}_{ij}$ は $i$ 番目の点を $j$ 番目のクラスタに割り当てる重み（確率）)
  * `iterations::Int`: 実行されたアルゴリズムの反復回数
  * `converged::Bool`: 手続きが収束したかどうか
