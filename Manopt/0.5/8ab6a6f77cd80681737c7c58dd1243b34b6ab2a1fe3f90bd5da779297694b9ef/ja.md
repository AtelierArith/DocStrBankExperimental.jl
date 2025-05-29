```
StopWhenSwarmVelocityLess <: StoppingCriterion
```

スワームの速度が閾値未満のときの[`particle_swarm`](@ref)の停止基準。

# フィールド

  * `threshold`:      閾値
  * `at_iteration`:   停止基準が（最後に）満たされたイテレーションを保存
  * `reason`:         停止基準が満たされた理由を保存、詳細は[`get_reason`](@ref)を参照
  * `velocity_norms`: ノルムを計算する前に速度のノルムを保存するための中間ベクトル

# コンストラクタ

```
StopWhenSwarmVelocityLess(tolerance::Float64)
```

特定の`tolerance`で停止基準を初期化します。
