```
GateData
```

すべてのゲートインデックスとデータを格納するオブジェクトです。

# フィールド

  * `gate_indices::Vector{GateIndex}`: すべてのゲートのインデックス。
  * `G::Int32`: ゲートの数。
  * `N::Int32`: インデックスの数。
  * `N_pad::Int32`: パディングされたインデックスの数。
  * `N_marginal::Int32`: マージナルインデックスの数。
  * `N_pad_marginal::Int32`: パディングされたマージナルインデックスの数。
  * `N_relative::Int32`: 相対インデックスの数。
  * `N_pad_relative::Int32`: パディングされた相対インデックスの数。
  * `combined::Bool`: Pauli X、Y、および Z 基底の SPAM ノイズを同じものとして扱うかどうか。
  * `strict::Bool`: ゲートが加法的または相対的精度で推定可能と見なされるかどうかに厳密であるかどうか。
