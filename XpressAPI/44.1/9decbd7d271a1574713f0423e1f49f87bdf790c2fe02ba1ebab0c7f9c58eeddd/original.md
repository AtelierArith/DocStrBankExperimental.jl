```
XPRS_bo_setpriority(bo, priority)::Nothing
```

Sets the priority value of a user branching object.

# Arguments

  * `bo::XPRSbranchobject`: The user branching object.
  * `priority::Integer`: The new priority value to assign to the branching object, which must be a number from 0 to 1000.

See also the documentation of the correponding function [XPRS*bo*setpriority](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRS_bo_setpriority.html) in the C API.
