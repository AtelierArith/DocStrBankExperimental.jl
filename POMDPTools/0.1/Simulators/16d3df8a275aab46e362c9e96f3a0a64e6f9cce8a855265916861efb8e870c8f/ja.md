```
RolloutSimulator(rng, max_steps)
RolloutSimulator(; <keyword arguments>)
```

報酬を返す高速シミュレーター

シミュレーションは次のいずれかの条件で終了します。

1. 終端状態に達した場合（`isterminal()`によって判断される）または
2. 割引率が`eps`と同じくらい小さくなった場合、または
3. max_stepsが実行された場合

# キーワード引数:

  * rng::AbstractRNG (デフォルト: Random.default_rng()) - 使用する乱数生成器。
  * eps::Float64 (デフォルト: 0.0) - 小さな数; γᵗがこの値より小さくなると、シミュレーションは終了します。ここで、γは割引率、tは時間ステップです。
  * max_steps::Int (デフォルト: typemax(Int)) - シミュレーションする最大ステップ数。

# 使用法（オプション引数は角括弧内）:

```
ro = RolloutSimulator()
history = simulate(ro, pomdp, policy, [updater [, init_belief [, init_state]]])
```

参照: [`HistoryRecorder`](@ref), [`run_parallel`](@ref)
