```
struct SimulationConfig{I, S, V<:VarianceReductionStrategy, TSeeds}
```

モンテカルロシミュレーションのための設定。

# フィールド

  * `trajectories`: モンテカルロパスの数。
  * `steps`: 各シミュレーションの時間ステップの数。
  * `variance_reduction`: 分散を減少させるための戦略（例：`Antithetic()`）。
  * `seeds`: 再現性のためにシミュレーションを初期化するために使用されるRNGシードのベクター。
