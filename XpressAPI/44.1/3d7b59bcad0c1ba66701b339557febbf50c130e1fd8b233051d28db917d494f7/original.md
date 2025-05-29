```
XPRSgetstringattrib(prob, attrib, maxbytes)::value, nbytes
```

Enables users to recover the values of various string problem attributes.

Problem attributes are set during loading and optimization of a problem.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `attrib::Integer`: Problem attribute whose value is to be returned.
  * `maxbytes::Integer`: Maximum number of bytes to be written into the cgval argument.

# Return values

  * `value::AbstractString`: Pointer to a string where the value of the attribute (plus null terminator) will be returned.
  * `nbytes::Int32`: Returns the length of the string control including the null terminator.

See also the documentation of the correponding function [XPRSgetstringattrib](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetstringattrib.html) in the C API.
