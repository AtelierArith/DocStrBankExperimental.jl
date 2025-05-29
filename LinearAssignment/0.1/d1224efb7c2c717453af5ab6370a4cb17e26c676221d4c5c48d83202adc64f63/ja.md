```
linear_assignment(
    cost::Union{SMatrix{M, N, T}, MMatrix{M, N, T}},
    early_exit::Bool = true
) -> Tuple{
    SVector{N, UInt8},  # 列のための割り当てられた行インデックス, cost[I[j], j]
    SVector{M, UInt8},  # 行のための割り当てられた列インデックス, cost[i, J[i]]
    SVector{M, T},      # 双対行変数
    SVector{N, T},      # 双対列変数
    Bool                # 割り当てが実現可能か
}
```

修正されたジョンカー・フォルゲナントアルゴリズムを使用して線形割り当て問題を解決します [1]。

割り当てのコストは `compute_cost(cost, I)` を使用して計算できます。

### 引数

  * `cost::Union{SMatrix{M, N, T}, MMatrix{M, N, T}}`: 矩形コスト行列
  * `early_exit::Bool = true`: 不可解性が検出されるとすぐに終了

### 戻り値

  * `SVector{N, UInt8}`: 列のための割り当てられた行インデックス
  * `SVector{M, UInt8}`: 行のための割り当てられた列インデックス
  * `SVector{M, T}`: 双対行変数
  * `SVector{N, T}`: 双対列変数
  * `Bool`: 割り当てが実現可能か

### 参考文献

[1] DF Crouse. 2D矩形割り当てアルゴリズムの実装について.     IEEE Transactions on Aerospace and Electronic Systems, 52(4):1679-1696,     2016年8月, DOI:10.1109/TAES.2016.140952
