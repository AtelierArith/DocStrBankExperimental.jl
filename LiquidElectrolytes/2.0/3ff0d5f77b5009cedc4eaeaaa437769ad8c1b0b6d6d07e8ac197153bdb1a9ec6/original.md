```
 cvsweep(
      sys;
      voltages=SawTooth(),
      periods=1,
      solver_kwargs...,
      )
```

Cyclic voltammetry sweep. By default, `voltages` given as a [`SawTooth`](@ref) function.

Calculate molar reaction rates and working electrode flux rates. Returns a [`CVSweepResult`](@ref).
