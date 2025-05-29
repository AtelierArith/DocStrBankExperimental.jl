```
growth_witness(df::DataFrame, [b];
    shift=:shift,
    norm=:norm,
    time_step=determine_constant_time_step(df),
    skip=0
)
growth_witness(sim::PMCSimulation, [b]; kwargs...)
```

Calculate the growth witness directly from the result (`DataFrame` or [`PMCSimulation`](@ref Main.Rimu.PMCSimulation)) of [`solve`](@ref CommonSolve.solve(::ProjectorMonteCarloProblem))ing a [`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem). The keyword arguments `shift` and `norm` can be used to change the names of the relevant columns.
