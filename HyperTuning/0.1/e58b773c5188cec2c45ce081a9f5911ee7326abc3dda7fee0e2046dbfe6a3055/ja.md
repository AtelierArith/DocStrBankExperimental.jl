```
Scenario(;
        parameters...,
        sampler    = default_sampler(),
        pruner     = default_pruner(),
        instances  = [1],
        max_trials = :auto,
        max_evals  = :auto,
        max_time   = :auto,
        verbose    = false,
        batch_size = max(nprocs(), Sys.CPU_THREADS),
    )
```

パラメータと予算を持つシナリオを定義します。

  * `sampler` 使用するサンプラー。
  * `pruner` 計算コストを削減するためのプルーナー。
  * `instances` 問題インスタンスを含む配列（イテレータ）。
  * `max_trials` [`optimize`](@ref) で評価される最大試行回数。
  * `max_evals` 最大関数評価回数。
  * `max_time` [`optimize`](@ref) での最大実行時間。
  * `verbose` 最適化中にメッセージを表示。
  * `batch_size` 各イテレーションで各インスタンスに対して評価される試行の数。
