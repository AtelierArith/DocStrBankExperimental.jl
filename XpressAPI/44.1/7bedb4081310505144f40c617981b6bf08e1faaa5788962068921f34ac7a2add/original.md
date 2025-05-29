```
XPRSgetobjintcontrol(prob, objidx, control)::value
```

Retrieves the value of a given integer control parameter associated with an objective.

These parameters control how the objective is treated during multi-objective optimization.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `objidx::Integer`: Index of the objective to query.
  * `control::XPRSObjControl`: Control parameter whose value is to be returned.

# Return value

  * `value::Int32`: Pointer to an integer where the control value will be returned.

See also the documentation of the correponding function [XPRSgetobjintcontrol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetobjintcontrol.html) in the C API.
