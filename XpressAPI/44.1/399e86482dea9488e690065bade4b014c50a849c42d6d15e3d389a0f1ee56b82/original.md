```
XPRSiiswrite(prob, iis, filename, filetype, flags)::prob
```

Writes an LP/MPS/CSV file containing a given Irreducible Infeasible Set (IIS).

If 0 is passed as the IIS number parameter, the initial infeasible subproblem is written.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `iis::Integer`: The ordinal number of the IIS to be written.
  * `filename::Union{Nothing,AbstractString}`: The name of the file to be created.
  * `filetype::Integer`: Type of file to be created: 0creates an lp/mps file containing the IIS as a linear programming problem; 1creates a comma separated (csv) file containing the description and supplementary information on the given IIS.
  * `flags::Union{Nothing,AbstractString}`: Flags passed to the XPRSwriteprob function.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSiiswrite](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSiiswrite.html) in the C API.
