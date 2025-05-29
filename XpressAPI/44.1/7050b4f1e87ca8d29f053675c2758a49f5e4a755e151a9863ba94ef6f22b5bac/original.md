```
XPRS_bo_addcuts(bo, branch, ncuts, cutind)::Nothing
```

Adds stored user cuts as new constraints to a branch of a user branching object.

# Arguments

  * `bo::XPRSbranchobject`: The user branching object to modify.
  * `branch::Integer`: The number of the branch to add the cuts for.
  * `ncuts::Integer`: Number of cuts to add.
  * `cutind::AbstractVector{Ptr{Cvoid}}`: Array of length `ncuts` containing the pointers to user cuts that should be added to the branch.

See also the documentation of the correponding function [XPRS*bo*addcuts](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRS_bo_addcuts.html) in the C API.
