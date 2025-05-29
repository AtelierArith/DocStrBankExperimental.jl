```
XPRSsetprobname(prob, probname)::prob
```

Sets the current default problem name.

This command is rarely used.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `probname::Union{Nothing,AbstractString}`: A string of up to MAXPROBNAMELENGTH characters containing the problem name.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSsetprobname](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsetprobname.html) in the C API.
