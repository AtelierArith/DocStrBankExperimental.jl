```
XPRSmipoptimize(prob, flags)::prob
```

This function begins a tree search for the optimal MIP solution.

The direction of optimization is given by OBJSENSE. The status of the problem when the function completes can be checked using MIPSTATUS.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `flags::Union{Nothing,AbstractString}`: Flags to pass to XPRSmipoptimize (MIPOPTIMIZE), which specifies how to solve the initial continuous problem where the MIP entities are relaxed.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSmipoptimize](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSmipoptimize.html) in the C API.
