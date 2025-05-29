```
XPRSreadbasis(prob, filename, flags)::prob
```

Instructs the Optimizer to read in a previously saved basis from a file.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `filename::Union{Nothing,AbstractString}`: A string of up to MAXPROBNAMELENGTH characters containing the file name from which the basis is to be read.
  * `flags::Union{Nothing,AbstractString}`: Flags to pass to `XPRSreadbasis` (`READBASIS`): CPLEX compatibility; (no effect, kept for compatibility); ninput basis file containing basic solution values; tinput a compact advanced form of the basis; vuse the provided filename verbatim, without appending the `.bss` extension; zread a compressed input file.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSreadbasis](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSreadbasis.html) in the C API.
