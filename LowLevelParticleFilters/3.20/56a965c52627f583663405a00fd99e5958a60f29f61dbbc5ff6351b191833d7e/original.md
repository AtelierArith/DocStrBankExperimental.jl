```
debugplot(pf, u, y, p=parameters(pf); runall=false, kwargs...)
```

Produce a helpful plot. For customization options (`kwargs...`), see `?pplot`.

  * `runall=false:` if true, runs all time steps befor displaying (faster), if false, displays the plot after each time step.

The generated plot becomes quite heavy. Initially, try limiting your input to 100 time steps to verify that it doesn't crash.

!!! note
    This function requires `using Plots` to be called before it is used.

