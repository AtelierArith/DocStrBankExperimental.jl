```
integrate(system,tf, Ut; rate=true, params, data)
```

Calculate test function integral for transient solution. If `rate=true` (default), calculate the flow rate (per second)  through the corresponding boundary. Otherwise, calculate the absolute amount. The result is a `nspec x (nsteps-1)` DiffEqArray.
