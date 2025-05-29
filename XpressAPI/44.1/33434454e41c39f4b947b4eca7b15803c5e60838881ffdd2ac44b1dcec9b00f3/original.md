```
XPRSreadprob(prob, filename, flags)::prob
```

Reads an (X)MPS or LP format matrix from file.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `filename::Union{Nothing,AbstractString}`: The path and file name from which the problem is to be read.
  * `flags::Union{Nothing,AbstractString}`: Flags to be passed: lonly `filename.lp` is searched for; vuse the provided filename verbatim, without appending the `.mps`, `.mat` or `.lp` extension; zread a compressed input file.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSreadprob](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSreadprob.html) in the C API.
