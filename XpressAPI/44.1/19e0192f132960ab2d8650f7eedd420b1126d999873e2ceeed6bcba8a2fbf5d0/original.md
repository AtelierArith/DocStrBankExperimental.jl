```
XPRSgetstringcontrol(prob, control, maxbytes)::value, nbytes
```

Returns the value of a given string control parameters.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `control::Integer`: Control parameter whose value is to be returned.
  * `maxbytes::Integer`: Maximum number of bytes to be written into the value argument.

# Return values

  * `value::AbstractString`: Pointer to a string where the value of the control (plus null terminator) will be returned.
  * `nbytes::Int32`: Returns the length of the string control including the null terminator.

See also the documentation of the correponding function [XPRSgetstringcontrol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetstringcontrol.html) in the C API.
