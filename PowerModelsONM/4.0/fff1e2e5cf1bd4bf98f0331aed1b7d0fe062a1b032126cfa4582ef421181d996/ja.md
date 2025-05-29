```
optimize_switches!(args::Dict{String,<:Any})::Dict{String,Any}
```

スイッチの状態を最適化します（したがって、負荷を軽減するかどうか）をインプレースで行い、[`entrypoint`](@ref entrypoint)で使用するために、[`optimize_switches`]を使用します。

LPUBFDiagPowerModel (LinDist3Flow)を使用し、したがって`args["solvers"]["misocp_solver"]`を指定する必要があります。
