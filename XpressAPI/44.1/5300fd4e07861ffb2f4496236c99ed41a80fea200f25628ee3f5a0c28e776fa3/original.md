```
XPRSreadbinsol(prob, filename, flags)::prob
```

Reads a solution from a binary solution file.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `filename::Union{Nothing,AbstractString}`: A string of up to MAXPROBNAMELENGTH characters containing the file name from which the solution is to be read.
  * `flags::Union{Nothing,AbstractString}`: Flags to pass to `XPRSreadbinsol` (`READBINSOL`): mload the solution as a solution for the MIP; xload the solution as a solution for the LP; vuse the provided filename verbatim, without appending the `.sol` extension; zread a compressed input file.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSreadbinsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSreadbinsol.html) in the C API.
