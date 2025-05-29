```
ProjectionParameters(; kwargs...)
```

プロジェクション手順のパラメータを保持するための型です。以下のパラメータが利用可能です：

  * `strategy = ExponentialFamilyProjection.DefaultStrategy()`: 勾配を計算するために使用する戦略。
  * `niterations = 100`: 最適化手順の反復回数。
  * `tolerance = 1e-6`: 勾配のノルムに対する許容誤差。
  * `stepsize = ConstantLength(0.1)`: 最適化手順のステップサイズ。`Manopt.jl`からのステップサイズを受け入れます。
  * `seed`: オプション; `rng`のためのシード
  * `rng`: オプション; 擬似乱数生成器
  * `direction = BoundedNormUpdateRule(static(1.0)`: 方向更新ルール。`Manopt.jl`からの`Manopt.DirectionUpdateRule`を受け入れます。
