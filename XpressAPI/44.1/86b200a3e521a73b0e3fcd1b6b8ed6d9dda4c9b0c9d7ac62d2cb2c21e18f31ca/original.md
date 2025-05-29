```
XPRSwritebinsol(prob, filename, flags)::prob
```

Writes the current MIP or LP solution to a binary solution file for later input into the Optimizer.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `filename::Union{Nothing,AbstractString}`: A string of up to MAXPROBNAMELENGTH characters containing the file name to which the solution is to be written.
  * `flags::Union{Nothing,AbstractString}`: Flags to pass to `XPRSwritebinsol` (`WRITEBINSOL`): moutput the MIP solution; xoutput the LP solution; vuse the provided filename verbatim, without appending the `.sol` extension; zcompress the output file.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSwritebinsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSwritebinsol.html) in the C API.
