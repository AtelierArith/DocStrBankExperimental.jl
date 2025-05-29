```
struct MonteCarlo{P<:PriceDynamics, S<:SimulationStrategy, C<:SimulationConfig}
```

Monte Carlo pricing method combining price dynamics, simulation strategy, and configuration.

# Fields

  * `dynamics`: The model for asset price dynamics.
  * `strategy`: Numerical simulation method.
  * `config`: Simulation configuration (paths, steps, seeds, etc.).
