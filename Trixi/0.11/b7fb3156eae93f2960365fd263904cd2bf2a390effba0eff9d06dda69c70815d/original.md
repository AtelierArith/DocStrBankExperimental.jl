```
semidiscretize(semi::SemidiscretizationHyperbolicParabolic, tspan)
```

Wrap the semidiscretization `semi` as a split ODE problem in the time interval `tspan` that can be passed to `solve` from the [SciML ecosystem](https://diffeq.sciml.ai/latest/). The parabolic right-hand side is the first function of the split ODE problem and will be used by default by the implicit part of IMEX methods from the SciML ecosystem.
