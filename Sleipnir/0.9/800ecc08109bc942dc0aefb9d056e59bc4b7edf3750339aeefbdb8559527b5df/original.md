```
    Parameters(; physical::PhysicalParameters = PhysicalParameters(), simulation::SimulationParameters = SimulationParameters())
```

Constructs a `Parameters` object with the given physical and simulation parameters.

# Arguments

  * `physical::PhysicalParameters`: An instance of `PhysicalParameters` (default: `PhysicalParameters()`).
  * `simulation::SimulationParameters`: An instance of `SimulationParameters` (default: `SimulationParameters()`).

# Returns

  * A `Parameters` object initialized with the provided physical and simulation parameters.

# Notes

  * If `simulation.multiprocessing` is enabled, multiprocessing is configured with the specified number of workers.
