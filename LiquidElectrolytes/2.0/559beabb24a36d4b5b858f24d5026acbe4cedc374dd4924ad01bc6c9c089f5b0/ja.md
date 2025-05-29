```julia
mutable struct CVSweepResult <: LiquidElectrolytes.AbstractSimulationResult
```

[`cvsweep`](@ref) の結果タイプ。

フィールド:

  * `voltages::Any`: 電圧のベクトル
  * `times::Any`: 時間のベクトル
  * `j_reaction::Any`: 作動電極のモル反応速度
  * `j_bulk::Any`: バルクモルフラックス
  * `j_we::Any`: 作動電極のモルフラックス
  * `tsol::Any`: 過渡解

アクセスメソッド: [`voltages`](@ref), [`currents`](@ref)  [`voltages_currents`](@ref)
