```
IntervalConstantSolver(; θ = 0.5, timestep)
```

区間ごとに定数の `ScalarGradient` に特化した BTPDE ソルバー、例えば [`PGSE`](@ref)、[`DoublePGSE`](@ref)。他の勾配に対してはエラーを発生させます。
