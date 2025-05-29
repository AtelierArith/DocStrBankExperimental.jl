```
simulate(cp::AbstractControlProblem, args...; kwargs...)
```

Simulate a controlled system for a family of random trajectories.

### Input

  * `cp`           – controlled problem
  * `trajectories` – (optional, default: `10`) number of simulated trajectories

### Output

An object of type `EnsembleSimulationSolution`.

### Notes

This function uses the ensemble simulations feature from [`OrdinaryDiffEq.jl`](https://github.com/SciML/OrdinaryDiffEq.jl).
