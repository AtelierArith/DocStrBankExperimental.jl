```
SolverTrace(num_steps, i, print_interval, io, progress, columns, callbacks)
```

Represents a solver trace for `num_steps` iterations, `i` being the current one. Each time [`next!`](@ref) is called, `i` is incremented by one, and if a multiple of `print_interval` is reached, a line is printed in the trace. Optionally (default), a `ProgressMeter.Progress` is shown as well, providing progress information between solver trace printouts.
