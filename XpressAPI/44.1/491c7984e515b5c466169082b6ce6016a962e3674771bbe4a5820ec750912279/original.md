```
XPRSsave(prob)::prob
```

Saves the current data structures, i.e. matrices, control settings and problem attribute settings to file and terminates the run so that optimization can be resumed later.

# Arguments

  * `prob::XPRSprob`: The current problem.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSsave](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsave.html) in the C API.
