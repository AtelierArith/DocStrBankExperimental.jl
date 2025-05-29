```
LSM(dynamics::PriceDynamics, strategy::SimulationStrategy, config::SimulationConfig, degree::Int)
```

Constructs an `LSM` pricing method with polynomial regression and Monte Carlo simulation.

# Arguments

  * `dynamics`: Price dynamics.
  * `strategy`: Simulation strategy.
  * `config`: Monte Carlo configuration.
  * `degree`: Degree of polynomial regression.

# Returns

  * An `LSM` instance.
