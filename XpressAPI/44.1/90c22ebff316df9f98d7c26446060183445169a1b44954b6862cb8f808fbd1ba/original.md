```
XPRStunerreadmethod(prob, methodfile)::prob
```

This function loads a user defined tuner method from the given file.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `methodfile::Union{Nothing,AbstractString}`: The method file name, from which the tuner can load a user-defined tuner method.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRStunerreadmethod](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRStunerreadmethod.html) in the C API.
