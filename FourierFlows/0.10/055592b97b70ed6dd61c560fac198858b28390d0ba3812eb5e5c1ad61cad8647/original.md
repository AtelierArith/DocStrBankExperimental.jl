```
FilteredAB3TimeStepper(equation::Equation, dev::Device=CPU(); filterkwargs...)
```

Construct a 3rd order Adams-Bashforth timestepper with spectral filtering for `equation` on device `dev`.
