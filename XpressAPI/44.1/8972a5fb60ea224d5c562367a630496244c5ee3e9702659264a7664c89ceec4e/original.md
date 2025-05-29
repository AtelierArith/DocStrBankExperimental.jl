```
XPRSdelobj(prob, objidx)::prob
```

Removes an objective function from a multi-objective problem.

Any objectives with `index > objidx` will be shifted down. Deleting the last objective function in the problem causes all the objective coefficients to be zeroed, but `OBJECTIVES` remains set to `1`.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `objidx::Integer`: Index of the objective to remove.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSdelobj](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSdelobj.html) in the C API.
