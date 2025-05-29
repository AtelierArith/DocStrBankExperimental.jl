```
LinDistFlow.add_variables(m::JuMP.AbstractModel, p::Inputs{MultiPhase})
```

定義: Pj, Qj, Pij, Qij, vsqrd

TODO:

  * 現在はインデックス付きのバス/エッジ、フェーズ、時間
  * しかし、BranchFlowModel MultiPhaseに合わせて: 時間、バス/エッジ、フェーズ（広いものから狭いものへ）
  * そして、CommonOPFで変数コンテナを標準化
  * しかし、ネストされたDictを使用すると変数の構築が遅くなる、なぜなら一度に一つを作成しなければならないから（これはMultiPhase BranchFlowModelでは必要だった） - しかし、大した問題ではないかもしれない
