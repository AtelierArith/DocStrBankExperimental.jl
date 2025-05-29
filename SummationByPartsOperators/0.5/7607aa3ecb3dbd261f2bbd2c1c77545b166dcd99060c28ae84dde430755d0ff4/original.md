```
semidiscretize(u0func, semi::AbstractSemidiscretization, tspan)
```

Apply the semidiscretization `semi` to the initial data given by `u0func` and return an `ODEProblem` with time span `tspan`.
