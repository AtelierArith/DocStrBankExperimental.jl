```
Problem(num_layers::Int, local_fields::Vector{Real}, couplings::Matrix{Real}, driver)
```

QAOA回路の基本的な特性を保持するコンテナ。

  * `num_qubits::Int64`: QAOA回路の量子ビットの数。
  * `num_layers::Int64`: QAOA回路の層の数 $p$。
  * `local_fields::Vector{Real}`: イジング問題ハミルトニアンの局所（磁気）場。
  * `couplings::Matrix{Real}`: イジング問題ハミルトニアンの結合行列。
  * `edges::Any`: 結合行列によって指定されたグラフのエッジ。
  * `driver::Any`: QAOA回路のドライバー。デフォルトではパウリ行列 `X`。例えば、`[[X, X], [Y, Y]]` に設定することで、接続された量子ビットのすべてのペアに作用するドライバー$\hat X_i \hat X_j + \hat Y_i \hat Y_j$を取得できます。
