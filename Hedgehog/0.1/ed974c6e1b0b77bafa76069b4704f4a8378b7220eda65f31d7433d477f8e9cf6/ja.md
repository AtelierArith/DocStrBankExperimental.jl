```
struct MonteCarlo{P<:PriceDynamics, S<:SimulationStrategy, C<:SimulationConfig}
```

資産価格のダイナミクス、シミュレーション戦略、および構成を組み合わせたモンテカルロ価格設定手法。

# フィールド

  * `dynamics`: 資産価格ダイナミクスのモデル。
  * `strategy`: 数値シミュレーション手法。
  * `config`: シミュレーション構成（パス、ステップ、シードなど）。
