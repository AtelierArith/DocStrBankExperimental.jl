```
XPRSrestore(prob, probname, flags)::prob
```

Restores the Optimizer's data structures from a file created by XPRSsave (SAVE).

Optimization may then recommence from the point at which the file was created.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `probname::Union{Nothing,AbstractString}`: A string of up to MAXPROBNAMELENGTH characters containing the problem name.
  * `flags::Union{Nothing,AbstractString}`: Additional flags force (no effect, kept for compatibility); hDo not restore hardware information from the file; vuse the provided filename verbatim, without appending the `.svf` extension.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSrestore](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSrestore.html) in the C API.
