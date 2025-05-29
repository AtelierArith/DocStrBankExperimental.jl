```
semidiscretize(semi::Semidiscretization, tspan)
```

Wrap the semidiscretization `semi` as an ODE problem in the time interval `tspan` that can be passed to `solve` from the [SciML ecosystem](https://diffeq.sciml.ai/latest/).
