```
dmatrix, GProws, GPcols = ghwt_tf_init_2d(matrix::Matrix{Float64})

最初に行列をパーティションしてGProwsとGPcolsを取得します。その後、行列を2つの方向に拡張してdmatrixを取得します。
```

### 入力引数

  * `matrix::Matrix{Float64}`: 入力行列

### 出力引数

  * `GProws::GraphPart`: 行をサンプルとして使用したパーティショニング
  * `GPcols::GraphPart`: 列をサンプルとして使用したパーティショニング
  * `dmatrix::matrix{Float64}`: 行列の拡張係数
