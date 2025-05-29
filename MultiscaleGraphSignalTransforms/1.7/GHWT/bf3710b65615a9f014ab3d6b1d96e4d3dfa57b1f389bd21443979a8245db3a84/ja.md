```
(f, GS) = ghwt_synthesis(dvec::Matrix{Float64}, GP::GraphPart, BS::BasisSpec, G::GraphSig)
```

与えられたGHWT展開係数のベクトルとグラフ分割および基底の選択に関する情報をもとに、信号を再構成します。

### 入力引数

  * `dvec::Matrix{Float64}`: 選択された基底に対応する展開係数
  * `GP::GraphPart`: 入力GraphPartオブジェクト
  * `BS::BasisSpec`: 入力BasisSpecオブジェクト
  * `G::GraphSig`: 入力GraphSigオブジェクト

### 出力引数

  * `f::Matrix{Float64}`: 再構成された信号
  * `GS::GraphSig`: 再構成されたGraphSigオブジェクト
