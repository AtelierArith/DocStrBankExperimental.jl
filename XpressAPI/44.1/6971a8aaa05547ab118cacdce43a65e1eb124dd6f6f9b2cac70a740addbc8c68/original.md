```
XPRSwriteprtsol(prob, filename, flags)::prob
```

Writes the current solution to a fixed format ASCII file, problem_name `.prt`.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `filename::Union{Nothing,AbstractString}`: A string of up to MAXPROBNAMELENGTH characters containing the file name to which the solution is to be written.
  * `flags::Union{Nothing,AbstractString}`: Flags for `XPRSwriteprtsol` (`WRITEPRTSOL`) are: print the solution to the screen (via the message callback) instead of writing to a file; xwrite the LP solution instead of the current MIP solution; vuse the provided filename verbatim, without appending the `.prt` extension; zwrite a compressed output file; sinclude classical sensitivity analysis.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSwriteprtsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSwriteprtsol.html) in the C API.
