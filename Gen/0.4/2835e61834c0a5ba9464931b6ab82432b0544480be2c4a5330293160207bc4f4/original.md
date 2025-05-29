```
new_trace = map_optimize(trace, selection::Selection,
    max_step_size=0.1, tau=0.5, min_step_size=1e-16, verbose=false)
```

Perform backtracking gradient ascent to optimize the log probability of the trace over selected continuous choices.

Selected random choices must have support on the entire real line.
