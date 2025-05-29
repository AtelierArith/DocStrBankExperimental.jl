function HGLET*GHWT*Synthesis(dvec::Matrix{Float64},GP::GraphPart,BS::BasisSpec,trans::Array{Bool,2},G::GraphSig)

```
与えられたHGLETおよびGHWT展開係数のベクトル、グラフ分割に関する情報、基底の選択および対応する変換を使用して、信号を再構成します。
```

### 入力引数

  * `dvec`:   選択された基底に対応する展開係数
  * `GP`:     GraphPartオブジェクト
  * `BS`:     BasisSpecオブジェクト
  * `trans`:  HGLET-GHWTハイブリッド変換に使用される変換の仕様   00 = HGLET with L   01 = HGLET with Lrw   10 = HGLET with Lsym   11 = GHWT
  * `G`:      GraphSigオブジェクト

### 出力引数

  * `f`:      再構成された信号
  * `GS`:     再構成されたGraphSigオブジェクト
