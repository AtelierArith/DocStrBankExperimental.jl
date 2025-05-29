```
XPRSsetobjdblcontrol(prob, objidx, control, value)::prob
```

Sets the value of a given double control parameter associated with an objective.

These parameters control how the objective is treated during multi-objective optimization.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `objidx::Integer`: Index of the objective to modify.
  * `control::XPRSObjControl`: Control parameter whose value is to be modified.
  * `value::Float64`: Value to which the control parameter is to be set.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSsetobjdblcontrol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsetobjdblcontrol.html) in the C API.
