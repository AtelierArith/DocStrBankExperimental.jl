```
XPRSwriteslxsol(prob, filename, flags)::prob
```

Creates an ASCII solution file (`.slx`) using a similar format to MPS files.

These files can be read back into the Optimizer using the XPRSreadslxsol function.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `filename::Union{Nothing,AbstractString}`: A string of up to MAXPROBNAMELENGTH characters containing the file name to which the solution is to be written.
  * `flags::Union{Nothing,AbstractString}`: Flags to pass to `XPRSwriteslxsol` (`WRITESLXSOL`): lwrite the LP solution in case of a MIP problem; mwrite the MIP solution; puse full precision for numerical values (obsolete as this is now default behavior); sincluding slack variables; dLP solution only: including dual variables; rLP solution only: including reduced cost; vuse the provided filename verbatim, without appending the `.slx` extension; zcompress the output file.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSwriteslxsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSwriteslxsol.html) in the C API.
