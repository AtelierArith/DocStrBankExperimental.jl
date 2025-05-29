```
get_activepower_series(
        res::SimulationResults,
        name::String,
)
```

Function to obtain the active power output time series of a Dynamic Injection series out of the DAE Solution.

# Arguments

  * `res::SimulationResults` : Simulation Results object that contains the solution
  * `name::String` : Name to identify the specified device
