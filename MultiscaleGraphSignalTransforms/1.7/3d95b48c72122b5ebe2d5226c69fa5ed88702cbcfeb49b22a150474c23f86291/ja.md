```
function LPHGLET_Synthesis(dvec::Vector{Float64}, GP::GraphPart, BS::BasisSpec, G::GraphSig; gltype::Symbol = :L, ϵ::Float64 = 0.3)
```

ラップされたHGLET合成変換を実行します

### 入力引数

  * `dvec`: 選択した基底に対応する展開係数
  * `GP`: GraphPartオブジェクト
  * `BS`: BasisSpecオブジェクト
  * `G`: GraphSigオブジェクト
  * `gltype`: :Lまたは:Lsym、使用される固有ベクトルを示します
  * `ϵ`: 相対アクション帯域幅（デフォルト: 0.3）

### 出力引数

  * `f`: 再構成された信号
  * `GS`: 再構成されたGraphSigオブジェクト
