```
XPRSgetstrattrib(prob, attrib)::value
```

Enables users to recover the values of various string problem attributes.

Problem attributes are set during loading and optimization of a problem.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `attrib::Integer`: Problem attribute whose value is to be returned.

# Return value

  * `value::AbstractString`: Pointer to a string where the value of the attribute (plus null terminator) will be returned.

See also the documentation of the correponding function [XPRSgetstrattrib](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetstrattrib.html) in the C API.
