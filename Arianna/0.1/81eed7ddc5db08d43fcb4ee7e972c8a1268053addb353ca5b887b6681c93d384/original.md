```
Simulation(chains, algorithm_list, steps; path="data", verbose=false)
```

Create a new `Simulation` instance from a list of algorithm constructors.

# Arguments

  * `chains`: Vector of independent Arianna systems.
  * `algorithm_list`: List of algorithm constructors.
  * `steps`: Number of MC sweeps.
  * `path="data"`: Simulation path.
  * `verbose=false`: Flag for verbose output.
