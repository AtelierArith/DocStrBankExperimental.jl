```julia
struct DLCapSweepResult <: LiquidElectrolytes.AbstractSimulationResult
```

[`dlcapsweep`](@ref) の結果データ型

  * `voltages::Vector`: 電圧のベクトル
  * `dlcaps::Vector`: 二重層キャパシタンスのベクトル
  * `solutions::Vector`: 解のベクトル

アクセスメソッド: [`voltages`](@ref), [`voltages_solutions`](@ref),  [`voltages_dlcaps`](@ref)
