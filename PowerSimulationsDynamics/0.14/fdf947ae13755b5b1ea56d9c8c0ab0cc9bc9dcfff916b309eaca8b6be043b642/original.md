```
get_field_voltage_series(
        res::SimulationResults,
        name::String,
)
```

Function to obtain the field voltage time series of a Dynamic Generator out of the DAE Solution.

# Arguments

  * `res::SimulationResults` : Simulation Results object that contains the solution
  * `name::String` : Name to identify the specified device
