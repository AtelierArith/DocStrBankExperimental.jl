```
struct SimulationConfig{I, S, V<:VarianceReductionStrategy, TSeeds}
```

Configuration for Monte Carlo simulations.

# Fields

  * `trajectories`: Number of Monte Carlo paths.
  * `steps`: Number of time steps in each simulation.
  * `variance_reduction`: Strategy to reduce variance (e.g., `Antithetic()`).
  * `seeds`: Vector of RNG seeds used to initialize simulations for reproducibility.
