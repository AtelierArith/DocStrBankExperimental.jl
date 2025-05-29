```julia
PeriodicCallback(f, Δt::Number; phase = 0, initial_affect = false,
    final_affect = false,
    kwargs...)
```

`PeriodicCallback` は、関数が統合時間に基づいて定期的に呼び出されるべき場合に使用できます（壁時間ではなく）、すなわち `t = tspan[1]`、`t = tspan[1] + Δt`、`t = tspan[1] + 2Δt` などです。

非ゼロの `phase` が提供されると、コールバックの呼び出しは `phase` 時間単位だけシフトされます。つまり、呼び出しは `t = tspan[1] + phase`、`t = tspan[1] + phase + Δt`、`t = tspan[1] + phase + 2Δt` などで発生します。

このコールバックは、例えば、固定レートで動作する連続時間システムの離散時間コントローラをモデル化するために使用できます。

## 引数

  * `f` は定期的に呼び出される `affect!(integrator)` 関数
  * `Δt` は周期です

## キーワード引数

  * `phase` は位相オフセットです
  * `initial_affect` は初期時刻に影響を適用するかどうかで、デフォルトは `false` です
  * `final_affect` は最終時刻に影響を適用するかどうかで、デフォルトは `false` です
  * `kwargs` は `DiscreteCallback` コンストラクタが受け入れるキーワード引数です。
