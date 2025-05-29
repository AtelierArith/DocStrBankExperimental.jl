```
XPRSsaveas(prob, sSaveFileName)::prob
```

Saves the current data structures, i.e. matrices, control settings and problem attribute settings to file and terminates the run so that optimization can be resumed later.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `sSaveFileName::Union{Nothing,AbstractString}`: The name of the file (without .svf) to save to.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSsaveas](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsaveas.html) in the C API.
