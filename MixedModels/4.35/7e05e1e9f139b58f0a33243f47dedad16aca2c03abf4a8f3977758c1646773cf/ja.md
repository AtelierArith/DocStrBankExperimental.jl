```
ReMat{T,S} <: AbstractMatrix{T}
```

ランダム効果項によって生成されたモデル行列の一部。

# フィールド

  * `trm`: `StatsModels.CategoricalTerm`としてのグルーピング因子
  * `refs`: グルーピング因子のレベルへのインデックスを持つ`Vector{Int32}`
  * `levels`: グルーピング因子のレベル
  * `cnames`: 項の左辺によって生成されたモデル行列の列の名前
  * `z`: 項の左辺によって生成されたモデル行列の転置
  * `wtz`: `z`の重み付きコピー（`z`と`wtz`は非重み付きの場合同じオブジェクト）
  * `λ`: サイズ`S×S`の`LowerTriangular`または`Diagonal`行列
  * `inds`: `λ`の潜在的な非ゼロの線形インデックスを持つ`Vector{Int}`
  * `adjA`: `SparseMatrixCSC{T}`としての行列の随伴
  * `scratch`: `Matrix{T}`
