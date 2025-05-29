```
get_reactivepower_series(
        res::SimulationResults,
        name::String,
)
```

Function to obtain the reactive power output time series of a Dynamic Injection series out of the DAE Solution.

# Arguments

  * `res::SimulationResults` : Simulation Results object that contains the solution
  * `name::String` : Name to identify the specified device
