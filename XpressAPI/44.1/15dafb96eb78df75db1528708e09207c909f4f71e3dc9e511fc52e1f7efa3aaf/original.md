```
XPRSwriteprob(prob, filename, flags)::prob
```

Writes the current problem to an MPS or LP file.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `filename::Union{Nothing,AbstractString}`: A string of up to MAXPROBNAMELENGTH characters to contain the file name to which the problem is to be written.
  * `flags::Union{Nothing,AbstractString}`: Flags, which can be one or more of the following: output in a format compatible with CPLEX; oone element per line; noutput the scaled problem; sscrambled vector names; loutput in LP format; poutput values in full precision (obsolete as this is now default behavior); tomit the Xpress header in LP format; vuse the provided filename verbatim, without appending the `.mps` or `.lp` extension; zcompress the output file.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSwriteprob](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSwriteprob.html) in the C API.
