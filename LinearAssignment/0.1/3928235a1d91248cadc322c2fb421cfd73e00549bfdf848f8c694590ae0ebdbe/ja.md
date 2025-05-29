```
linear_assignment!(
    L::LAWorkspaceCSC{Tv},
    cost::SparseMatrixCSC{Tc},
    early_exit::Bool = true,
    reset::Bool = true
) -> LAWorkspaceCSC{Tv}

linear_assignment!(
    L::LAWorkspaceCSC{Tv},
    m::Integer,
    n::Integer,
    colptr::AbstractVector{<:Integer},
    rowval::AbstractVector{<:Integer},
    nzval::AbstractVector{Tc},
    early_exit::Bool = true,
    reset::Bool = true
) -> LAWorkspaceCSC{Tv}
```

修正されたジョンカー-フォルゲナントアルゴリズムを使用してスパース線形割り当て問題を解決します [1]。

割り当てのコストは `compute_cost(L, cost)`、`compute_cost(L, m, n, colptr, rowval, nzval)` を使用して計算できます。割り当てられた行と列のインデックスは、LAWorkspaceCSC.I、J にそれぞれ見つけることができます。

### 引数

  * `L::LAWorkspaceCSC{Tv}`: ワークスペース構造体
  * `cost::SparseMatrixCSC{Tc}`: スパース矩形コスト行列
  * `early_exit::Bool = true`: 不可解性が検出され次第終了
  * `reset::Bool = true`: 割り当てられたインデックスと双対ベクトルをゼロにする

### 戻り値

  * `LAWorkspaceCSC{T}`: 割り当てられたインデックス、双対ベクトルなどを含む構造体。

### 参考文献

[1] DF Crouse. 2D矩形割り当てアルゴリズムの実装について。 IEEE Transactions on Aerospace and Electronic Systems, 52(4):1679-1696, 2016年8月, DOI:10.1109/TAES.2016.140952
