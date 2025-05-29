```
XPRSwritebasis(prob, filename, flags)::prob
```

Writes the current basis to a file for later input into the Optimizer.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `filename::Union{Nothing,AbstractString}`: A string of up to MAXPROBNAMELENGTH characters containing the file name from which the basis is to be written.
  * `flags::Union{Nothing,AbstractString}`: Flags to pass to `XPRSwritebasis` (`WRITEBASIS`): scrambled vector names; output values in hexadecimal; output in a format compatible with CPLEX; ioutput the internal presolved basis; toutput a compact advanced form of the basis; noutput basis file containing current solution values; houtput values in single precision; poutput values in full precision (obsolete as this is now default behavior); vuse the provided filename verbatim, without appending the `.bss` extension; zcompress the output file.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSwritebasis](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSwritebasis.html) in the C API.
