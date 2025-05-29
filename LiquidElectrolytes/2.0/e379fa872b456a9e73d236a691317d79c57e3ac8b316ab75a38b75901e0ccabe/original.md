```
 ivsweep(
      sys;
      voltages = (-0.5:0.1:0.5) * ufac"V",
      store_solutions = false,
      solver_kwargs...,
      )
```

Steady state voltammetry.

Calculate molar reaction rates and bulk flux rates for each voltage in `voltages`. Returns a [`IVSweepResult`](@ref).
