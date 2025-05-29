```
XPRSgetobjdblcontrol(prob, objidx, control)::value
```

Retrieves the value of a given double control parameter associated with an objective function.

These parameters control how the objective is treated during multi-objective optimization.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `objidx::Integer`: Index of the objective to query.
  * `control::XPRSObjControl`: Control parameter whose value is to be returned.

# Return value

  * `value::Float64`: Pointer to a double where the control value will be returned.

See also the documentation of the correponding function [XPRSgetobjdblcontrol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetobjdblcontrol.html) in the C API.
