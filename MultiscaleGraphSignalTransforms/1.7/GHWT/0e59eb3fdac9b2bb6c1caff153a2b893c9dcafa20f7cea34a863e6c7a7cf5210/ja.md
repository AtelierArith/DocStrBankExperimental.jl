```
dmatrix = ghwt_analysis!(G::GraphSig, GP::GraphPart = nothing, c2f::Bool = true)
```

GraphSigオブジェクト`G`に対して、GHWT展開係数の行列を生成します。

### 入力引数

  * `G::GraphSig`: 入力GraphSigオブジェクト
  * `GP::GraphPart`: 入力GraphPartオブジェクト（オプション）；この関数が実行された後、`GP`の`compinfo`、`tag`などが填充されます。

### 出力引数

  * `dmatrix::Array{Float64,3}`: 展開係数の3D配列（すなわち、各入力信号ベクトルに対する係数の行列；したがって、複数の入力信号に対して、係数は3D配列として整理されます）
