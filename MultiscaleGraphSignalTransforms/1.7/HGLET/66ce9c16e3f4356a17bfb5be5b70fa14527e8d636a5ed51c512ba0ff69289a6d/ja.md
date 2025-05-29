function HGLET_Synthesis(dvec::Vector{Float64}, GP::GraphPart, BS::BasisSpec,                          G::GraphSig; gltype::Symbol = :L)

### 入力引数

  * `dvec`: 選択した基底に対応する展開係数
  * `GP`: GraphPartオブジェクト
  * `BS`: BasisSpecオブジェクト
  * `G`: GraphSigオブジェクト
  * `gltype`: :L, :Lrw, または :Lsym、使用される固有ベクトルを示す

### 出力引数

  * `f`: 再構成された信号
  * `GS`: 再構成されたGraphSigオブジェクト
