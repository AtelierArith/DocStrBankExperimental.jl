```julia
run_simulation(config::HallThruster.Config; kwargs...)

```

**非推奨**。`run_simulation(::Config, ::SimParams; kwargs...)`を使用してください。

提供されたConfigオブジェクトを使用してHallスラスタシミュレーションを実行します。

## 引数

  * `config`: シミュレーションパラメータを含む`Config`。
  * `dt`: タイムステップ（秒単位）。典型的な値はO(10 ns)（1e-8秒）。
  * `duration`: シミュレーションを実行する時間（秒単位、シミュレーション時間、ウォールタイムではない）。典型的な実行時間はO(1 ms)（1e-3秒）。
  * `ncells`: 使用するセルの数。典型的な値は100 - 1000セル。
  * `nsave`: 保存するフレームの数。
