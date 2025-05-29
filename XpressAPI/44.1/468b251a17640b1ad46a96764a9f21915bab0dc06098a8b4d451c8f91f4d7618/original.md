```
XPRSgetintcontrol64(prob, control)::value
```

Enables users to recover the values of various integer control parameters

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `control::Integer`: Control parameter whose value is to be returned.

# Return value

  * `value::Int64`: Pointer to an integer where the value of the control will be returned.

See also the documentation of the correponding function [XPRSgetintcontrol64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetintcontrol64.html) in the C API.
