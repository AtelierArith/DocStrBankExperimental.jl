```
XPRStune(prob, flags)::prob
```

This function begins a tuner session for the current problem.

The tuner will solve the problem multiple times while evaluating a list of control settings and promising combinations of them. When finished, the tuner will select and set the best control setting on the problem. Note that the direction of optimization is given by OBJSENSE.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `flags::Union{Nothing,AbstractString}`: Flags to pass to XPRStune, which specify whether to tune the current problem as an LP or a MIP problem, and the algorithm for solving the LP problem or the initial LP relaxation of the MIP.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRStune](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRStune.html) in the C API.
