```
XPRSnlpoptimize(prob, flags)::prob
```

Maximize or minimize an SLP problem

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `flags::Union{Nothing,AbstractString}`: These have the same meaning as for `XPRSmaxim` and `XPRSminim`.

# Return value

  * `prob::XPRSprob`: The current SLP problem.

See also the documentation of the correponding function [XPRSnlpoptimize](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpoptimize.html) in the C API.
