```
XPRScopyprob(dest, src, name)::dest
```

Copies information defined for one problem to another.

# Arguments

  * `dest::XPRSprob`: The new problem pointer to which information is copied.
  * `src::XPRSprob`: The old problem pointer from which information is copied.
  * `name::Union{Nothing,AbstractString}`: A string of up to 1024 characters including `nothing` terminator containing the name for the problem copy.

# Return value

  * `dest::XPRSprob`: The new problem pointer to which information is copied.

See also the documentation of the correponding function [XPRScopyprob](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRScopyprob.html) in the C API.
