```
FilteredRK4TimeStepper(equation::Equation, dev::Device=CPU(); filterkwargs...)
```

Construct a 4th-order 5-stages 2-storage Runge-Kutta timestepper with spectral filtering for `equation` on device `dev`.
