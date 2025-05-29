```
SimData
```

Data structure containing the time series data for a simulation.

It is a collection of [`TSeries`](@ref) of the same frequency and containing data for the same range. When used for simulation, the range must include the initial conditions, the simulation range and the final conditions, although it could extend beyond that. It must contain time series for all variables and shocks in the model, in the same order as in the model object.
