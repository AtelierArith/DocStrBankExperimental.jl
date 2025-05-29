```
SolverTrace(num_steps[, column=CurrentStep(num_steps), columns...;
                        io=stdout, num_printouts=10, progress_meter=true,
                        print_interval, kwargs...])
```

Construct a [`SolverTrace`](@ref) for `num_steps` iterations, with the `columns` that are to appear in the solver trace. The solver trace is printed to `io`, `num_printouts` lines will appear; alternatively, the `print_interval` can be specified directly. Below the solver trace, a progressbar is displayed, unless `!progress_meter`. `kwargs...` are passed on to `ProgressMeter.Progress`.
