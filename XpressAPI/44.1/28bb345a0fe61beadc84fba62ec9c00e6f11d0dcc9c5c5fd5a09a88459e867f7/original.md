```
XPRSlpoptimize(prob, flags)::prob
```

This function begins a search for the optimal continuous (LP) solution.

The direction of optimization is given by OBJSENSE. The status of the problem when the function completes can be checked using LPSTATUS. Any MIP entities in the problem will be ignored.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `flags::Union{Nothing,AbstractString}`: Flags to pass to `XPRSlpoptimize` (`LPOPTIMIZE`).

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSlpoptimize](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSlpoptimize.html) in the C API.
