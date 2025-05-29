```
dmatrix = ghwt_tf_init_2d(matrix::Matrix{Float64}, GProws::GraphPart, GPcols::GraphPart)

最初に行をサンプルとして使用して行列を分割し、次に行列を2つの方向に拡張してdmatrixを取得します。
```

### 入力引数

  * `matrix::Matrix{Float64}`: 入力行列
  * `GProws::GraphPart`: 行をサンプルとして使用した分割
  * `GPcols::GraphPart`: 列をサンプルとして使用した分割

### 出力引数

  * `dmatrix::matrix{Float64}`: 行列の拡張係数
