```
tempered_sample([rng, ], model, sampler, N, inverse_temperatures; kwargs...)
OR
tempered_sample([rng, ], model, sampler, N, N_it; swap_strategy=SingleSwap(), kwargs...)
```

`model`から`N`サンプルを生成するために、提供された`sampler`の温度付きバージョンを使用します。いずれかの`inverse_temperatures`または`N_it`（および`swap_strategy`）を提供して生成します。

# キーワード引数

  * `N_burnin::Integer` バーンインステップは、チェーン間のスワップを試みる前に実行されます
  * `swap_strategy::AbstractSwapStrategy` チェーン間で逆温度をスワップする方法を指定します
  * `steps_per_swap::Integer` スワップの試行ごとに実行されるステップ数

# 参照

  * [`tempered`](@ref)
  * [`TemperedSampler`](@ref)
  * スワップ戦略の詳細については：

      * [`AbstractSwapStrategy`](@ref)
      * [`ReversibleSwap`](@ref)
      * [`NonReversibleSwap`](@ref)
      * [`SingleSwap`](@ref)
      * [`SingleRandomSwap`](@ref)
      * [`RandomSwap`](@ref)
      * [`NoSwap`](@ref)

```
