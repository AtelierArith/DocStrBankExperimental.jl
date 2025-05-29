```
XPRSreadslxsol(prob, filename, flags)::prob
```

Reads an ASCII solution file `.slx` created by the XPRSwriteslxsol function.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `filename::Union{Nothing,AbstractString}`: A string of up to MAXPROBNAMELENGTH characters containing the file name to which the solution is to be read.
  * `flags::Union{Nothing,AbstractString}`: Flags to pass to `XPRSreadslxsol` (`READSLXSOL`): non-breaking-whitespace conversion; lread the solution as an LP solution in case of a MIP problem; mread the solution as a solution for the MIP problem; aread multiple MIP solutions from the `.slx` file and add them to the MIP problem; vuse the provided filename verbatim, without appending the `.slx` extension; zread a compressed input file.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSreadslxsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSreadslxsol.html) in the C API.
