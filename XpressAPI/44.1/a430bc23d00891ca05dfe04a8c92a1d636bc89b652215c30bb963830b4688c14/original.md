```
XPRSoptimize(prob, flags)::solvestatus, solstatus
```

This function begins a search for the optimal solution of the problem.

The direction of optimization is given by OBJSENSE.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `flags::Union{Nothing,AbstractString}`: Flags to pass to `XPRSoptimize` (`OPTIMIZE`).

# Return values

  * `solvestatus::Int32`: The solve status after termination.
  * `solstatus::Int32`: The solution status after termination.

See also the documentation of the correponding function [XPRSoptimize](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSoptimize.html) in the C API.
