```
semidiscretize(semi::AbstractSemidiscretization, tspan, 
               restart_file::AbstractString)
```

Wrap the semidiscretization `semi` as an ODE problem in the time interval `tspan` that can be passed to `solve` from the [SciML ecosystem](https://diffeq.sciml.ai/latest/). The initial condition etc. is taken from the `restart_file`.
