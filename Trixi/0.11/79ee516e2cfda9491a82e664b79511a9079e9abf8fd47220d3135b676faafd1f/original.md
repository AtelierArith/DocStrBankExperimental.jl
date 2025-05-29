```
load_timestep!(integrator, restart_file::AbstractString)
```

Load the time step number saved in a `restart_file` and assign it to both the time step number and and the number of accepted steps (`iter` and `stats.naccept` in OrdinaryDiffEq.jl, respectively) in `integrator`.
