```
dvec = dmatrix2dvec(dmatrix::Array{Float64,3}, GP::GraphPart, BS::BasisSpec)
```

与えられた展開係数の行列をベクトルに変換します。この関数は、入力係数配列 `dmatrix` が粗から細への形式であることを前提としています。もし `BS.c2f == false` の場合、この関数は内部的に `dmatrix` を細から粗への形式に変換します。したがって、f2c `dmatrix` を提供すると、結果が間違ってしまい、その後の手続きでエラーが発生する可能性があります。

### 入力引数

  * `dmatrix::Array{Float64,3}`: 展開係数の行列
  * `GP::GraphPart`: 入力 GraphPart オブジェクト
  * `BS::BasisSpec`: 入力 BasisSpec オブジェクト

### 出力引数

  * `dvec::Matrix{Float64}`: 展開係数のベクトル
