```
(dvec, BS) = dmatrix2dvec(dmatrix::Array{Float64,3}, GP::GraphPart)
```

与えられた展開係数の行列をベクトルに変換します。

### 入力引数

  * `dmatrix::Array{Float64,3}`: 展開係数の行列
  * `GP::GraphPart`: 入力GraphPartオブジェクト
  * `BS::BasisSpec`: 入力BasisSpecオブジェクト

### 出力引数

  * `dvec::Matrix{Float64}`: 展開係数のベクトル
  * `BS::BasisSpec`: 出力BasisSpecオブジェクト
