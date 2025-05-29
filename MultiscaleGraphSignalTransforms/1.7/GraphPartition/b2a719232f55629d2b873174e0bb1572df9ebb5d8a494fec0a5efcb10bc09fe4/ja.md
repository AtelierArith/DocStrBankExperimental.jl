```
GProws, GPcols = partition_tree_matrixDhillon(matrix::Matrix{Float64})

行と列を再帰的に分割し、Dhillonが提案した二部モデルを使用して行列を分割します。「二部スペクトルグラフ分割を使用した文書と単語の共同クラスタリング」において。

```

### 入力引数

  * `matrix::Matrix{Float64}`: 入力行列

### 出力引数

  * `GProws::GraphPart`: サンプルとして行を使用した分割
  * `GPcols::GraphPart`: サンプルとして列を使用した分割
