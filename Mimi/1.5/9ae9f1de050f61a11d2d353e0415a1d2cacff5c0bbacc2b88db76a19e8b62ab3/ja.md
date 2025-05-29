```
set_models!(sim_inst::SimulationInstance{T}, models::Vector{M}) where {T <: AbstractSimulationData, M <: AbstractModel}
```

`sim_inst` が保持する SimulationDef で使用される `models` を設定します。
