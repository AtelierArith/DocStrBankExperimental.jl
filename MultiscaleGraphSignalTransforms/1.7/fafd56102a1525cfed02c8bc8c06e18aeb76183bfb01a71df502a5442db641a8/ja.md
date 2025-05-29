```
dmatrix = dvec2dmatrix(dvec::Matrix{Float64}, GP::GraphPart, BS::BasisSpec)
```

与えられた展開係数のベクトルを行列に変換します。

### 入力引数

  * `dvec::Matrix{Float64}`: 展開係数のベクトル
  * `GP::GraphPart`: GraphPartオブジェクト
  * `BS::BasisSpec`: BasisSpecオブジェクト

### 出力引数

  * `dmatrix::Array{Float64,3}`: 展開係数の行列のセット
