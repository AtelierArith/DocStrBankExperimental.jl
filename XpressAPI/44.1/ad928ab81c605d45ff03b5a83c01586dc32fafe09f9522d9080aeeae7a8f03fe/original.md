```
XPRSgetintattrib64(prob, attrib)::value
```

Enables users to recover the values of various integer problem attributes.

Problem attributes are set during loading and optimization of a problem.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `attrib::Integer`: Problem attribute whose value is to be returned.

# Return value

  * `value::Int64`: Pointer to an integer where the value of the problem attribute will be returned.

See also the documentation of the correponding function [XPRSgetintattrib64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetintattrib64.html) in the C API.
