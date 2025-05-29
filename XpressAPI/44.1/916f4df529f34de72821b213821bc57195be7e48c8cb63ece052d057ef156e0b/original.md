```
XPRSiisfirst(prob, mode)::status
```

Initiates a search for an Irreducible Infeasible Set (IIS) in an infeasible problem.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `mode::Integer`: The IIS search mode: 0stops after finding the initial infeasible subproblem; 1find an IIS, emphasizing simplicity of the IIS; 2find an IIS, emphasizing a quick result.

# Return value

  * `status::Int32`: The status after the search: 0success; 1feasible problem; 2error; 3timeout or interruption.

See also the documentation of the correponding function [XPRSiisfirst](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSiisfirst.html) in the C API.
