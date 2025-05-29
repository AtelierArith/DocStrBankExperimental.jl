```
linear_assignment(
    cost::SparseMatrixCSC{Tv},
    early_exit::Bool = true
) -> LAWorkspaceCSC{Tv}
```

修正されたジョンカー-フォルゲナントアルゴリズムを使用して、スパース線形割り当て問題を解決します [1]。

割り当てのコストは `compute_cost(L, cost)` を使用して計算できます。割り当てられた行と列のインデックスは、それぞれ LAWorkspaceCSC.I,J に見つけることができます。

### 引数

  * `cost::SparseMatrixCSC{Tv}`: スパースの長方形コスト行列
  * `early_exit::Bool = true`: 不可解性が検出され次第、すぐに終了

### 戻り値

  * `LAWorkspaceCSC{Tv}`: 割り当てられたインデックス、双対ベクトルなどを含む構造体。

### 参考文献

[1] DF Crouse. 2D長方形割り当てアルゴリズムの実装について。     IEEE Transactions on Aerospace and Electronic Systems, 52(4):1679-1696,     2016年8月, DOI:10.1109/TAES.2016.140952
