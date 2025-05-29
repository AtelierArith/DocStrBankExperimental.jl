```
FilteredRK4TimeStepper(equation::Equation, dev::Device=CPU(); filterkwargs...)
```

Construct a 4th-order Runge-Kutta timestepper with spectral filtering for `equation` on device `dev`.
