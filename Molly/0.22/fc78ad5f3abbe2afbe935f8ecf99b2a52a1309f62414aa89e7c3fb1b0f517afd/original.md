```
SteepestDescentMinimizer(; <keyword arguments>)
```

Steepest descent energy minimization.

# Arguments

  * `step_size::D=0.01u"nm"`: the initial maximum displacement.
  * `max_steps::Int=1000`: the maximum number of steps.
  * `tol::F=1000.0u"kJ * mol^-1 * nm^-1"`: the maximum force below which to   finish minimization.
  * `log_stream::L=devnull`: stream to print minimization progress to.
