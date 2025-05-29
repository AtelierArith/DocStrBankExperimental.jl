```
commandplot(pf, u, y, p=parameters(pf); kwargs...)
```

Produce a helpful plot. For customization options (`kwargs...`), see `?pplot`. After each time step, a command from the user is requested.

  * q: quit
  * s n: step `n` steps

!!! note
    This function requires `using Plots` to be called before it is used.

