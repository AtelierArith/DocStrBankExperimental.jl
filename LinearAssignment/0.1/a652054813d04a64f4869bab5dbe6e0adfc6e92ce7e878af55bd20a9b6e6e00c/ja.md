```
linear_assignment!(
    L::LAWorkspace{T},
    cost::AbstractMatrix{Tc},
    early_exit::Bool = true,
    reset::Bool = true
) -> LAWorkspace{T}
```

修正されたジョンカー・フォルゲナントアルゴリズムを使用して線形割り当て問題を解決します [1]。

割り当てのコストは `compute_cost(L, cost)` を使用して計算できます。割り当てられた行と列のインデックスは、それぞれ LAWorkspace.I,J にあります。

### 引数

  * `L::LAWorkspace{T}`: ワークスペース構造体
  * `cost::AbstractMatrix{Tc}`: 長方形コスト行列
  * `early_exit::Bool = true`: 不可解性が検出され次第、すぐに終了
  * `reset::Bool = true`: 割り当てられたインデックスと双対ベクトルをゼロにする

### 戻り値

  * `LAWorkspace{T}`: 割り当てられたインデックス、双対ベクトルなどを含む構造体。

### 参考文献

[1] DF Crouse. 2D長方形割り当てアルゴリズムの実装について。 IEEE Transactions on Aerospace and Electronic Systems, 52(4):1679-1696, 2016年8月, DOI:10.1109/TAES.2016.140952
