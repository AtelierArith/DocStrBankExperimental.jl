```julia
mutable struct IVSweepResult <: LiquidElectrolytes.AbstractSimulationResult
```

[`ivsweep`](@ref) の結果データ型

  * `voltages::Any`: 電圧のベクトル
  * `j_reaction::Any`: 作動電極のモル反応速度
  * `j_we::Any`: 作動電極のモルフラックス
  * `j_bulk::Any`: バルクモルフラックス
  * `solutions::Any`: 溶液のベクトル

アクセスメソッド: [`voltages`](@ref), [`currents`](@ref),  [`voltages_currents`](@ref), [`voltages_solutions`](@ref)
