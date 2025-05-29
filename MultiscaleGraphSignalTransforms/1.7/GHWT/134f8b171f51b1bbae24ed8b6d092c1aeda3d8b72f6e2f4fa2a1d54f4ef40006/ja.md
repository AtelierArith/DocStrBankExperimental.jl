```
ghwt_core!(GP::GraphPart, dmatrix::Array{Float64,3})
```

は、展開係数、タグ、および compinfo を生成する前方 GHWT 変換を実行します。

### 入力引数

  * `GP::GraphPart`: GraphPart オブジェクト（タグおよび compinfo データの有無にかかわらず）；この関数が実行された後、タグおよび compinfo は変更されます
  * `dmatrix::Array{Float64,3}`: 元の入力信号 `f` としてのみ最後の列が埋められた展開係数の行列；この関数が実行された後、この行列には GHWT 辞書に対する入力信号の全展開係数が含まれます
