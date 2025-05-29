```
(dvec, BS) = ghwt_bestbasis(dmatrix::Array{Float64,3}, GP::GraphPart; cfspec::Any, flatten::Any = 1.0)
```

c2fおよびf2cの最良基底の中から全体の最良基底を選択します

### 入力引数

  * `dmatrix::Array{Float64,3}`: 拡張係数の行列
  * `GP::GraphPart`: 入力GraphPartオブジェクト
  * `cfspec::Any`: 使用するコスト関数の仕様 (デフォルト: 1.0、すなわち1ノルム)
  * `flatten::Any`: ベクトル値データをスカラー値データにフラット化する方法 (デフォルト: 1.0、すなわち1ノルム)

### 出力引数

  * `dvec::Matrix{Float64}`: 最良基底に対応する拡張係数のベクトル
  * `BS::BasisSpec`: 最良基底を指定するBasisSpecオブジェクト
