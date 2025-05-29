```
growth_witness(df::DataFrame, [b];
    shift=:shift,
    norm=:norm,
    time_step=determine_constant_time_step(df),
    skip=0
)
growth_witness(sim::PMCSimulation, [b]; kwargs...)
```

[`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem)を[`solve`](@ref CommonSolve.solve(::ProjectorMonteCarloProblem))した結果（`DataFrame`または[`PMCSimulation`](@ref Main.Rimu.PMCSimulation)）から成長ウィットネスを直接計算します。キーワード引数`shift`と`norm`を使用して、関連する列の名前を変更できます。
