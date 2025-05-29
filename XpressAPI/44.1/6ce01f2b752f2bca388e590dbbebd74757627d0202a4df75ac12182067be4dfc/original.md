```
XPRSgetobjintattrib(prob, solveidx, attrib)::value
```

Retrieves the value of a given integer attribute associated with a multi-objective solve.

When solving a multi-objective problem, several objectives might be optimized in sequence. After each solve, the problem attributes are captured so that they can be queried afterwards.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `solveidx::Integer`: Index of the solve to query.
  * `attrib::Integer`: Problem attribute whose value is to be returned.

# Return value

  * `value::Int32`: Pointer to an integer where attribute value will be returned.

See also the documentation of the correponding function [XPRSgetobjintattrib](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetobjintattrib.html) in the C API.
