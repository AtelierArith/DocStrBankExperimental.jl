```
run!(fcm::FuzzyCognitiveMap, iterations::Int; tolerance::Float64=1e-6)
```

指定された回数の反復または収束するまでFCMシミュレーションを実行します。

# 引数

  * `fcm::FuzzyCognitiveMap`: シミュレートするFCM
  * `iterations::Int`: 実行する最大反復回数
  * `tolerance::Float64=1e-6`: 状態変化の収束閾値

# 戻り値

  * Vector{Float16}: シミュレーション後のFCMの最終状態

シミュレーションは、最大反復回数に達するか、状態の変化（L2ノルムで測定）が許容範囲を下回るまで停止します。
