```
Network(nodes::Vector{FDMnode}, elements::Vector{FDMelement}, loads::Vector{FDMload})
```

ノード、要素、および荷重のコレクションによって定義されるFDMネットワーク。

# フィールド

  * `nodes::Vector{FDMnode}` ネットワーク内のノードのコレクション
  * `elements::Vector{FDMelement}` ネットワーク内の要素のコレクション
  * `loads::Vector{FDMload}` ネットワーク内の外部荷重のコレクション
  * `q::Vector{<:Real}` 要素の力密度のベクトル [n_e × 1]
  * `Q::SparseMatrixCSC{Float64, Int64}` `q` の対角化されたスパース行列 [n*e × n*e]
  * `C::SparseMatrixCSC{Int64, Int64}` 要素/ノード接続行列 [n*e × n*n]
  * `N::Vector{Int64}` 自由ノードインデックスのベクトル
  * `F::Vector{Int64}` 固定ノードインデックスのベクトル
  * `Cn::SparseMatrixCSC{Int64, Int64}` 自由ノードの接続行列 = `C[:, N]`
  * `Cf::SparseMatrixCSC{Int64, Int64}` 固定ノードの接続行列 = `C[:, F]`
  * `P::Matrix{<:Real}` 外部荷重行列 [n_n × 3]
  * `Pn::Matrix{<:Real}` 自由ノードに適用される荷重 = `P[N, :]`
  * `xyz::Matrix{<:Real}` すべてのノードの位置 [n_n × 3]
