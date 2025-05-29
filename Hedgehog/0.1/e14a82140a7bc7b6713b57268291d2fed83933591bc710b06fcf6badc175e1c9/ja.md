```
LSM(dynamics::PriceDynamics, strategy::SimulationStrategy, config::SimulationConfig, degree::Int)
```

ポリノミアル回帰とモンテカルロシミュレーションを用いた`LSM`価格設定メソッドを構築します。

# 引数

  * `dynamics`: 価格のダイナミクス。
  * `strategy`: シミュレーション戦略。
  * `config`: モンテカルロ設定。
  * `degree`: ポリノミアル回帰の次数。

# 戻り値

  * `LSM`インスタンス。
