```
XPRSgetunbvec(prob)::seq
```

Returns the index vector which causes the primal simplex or dual simplex algorithm to determine that a matrix is primal or dual unbounded respectively.

# Arguments

  * `prob::XPRSprob`: The current problem.

# Return value

  * `seq::Int32`: Pointer to an integer where the vector causing the problem to be detected as being primal or dual unbounded will be returned.

See also the documentation of the correponding function [XPRSgetunbvec](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetunbvec.html) in the C API.
