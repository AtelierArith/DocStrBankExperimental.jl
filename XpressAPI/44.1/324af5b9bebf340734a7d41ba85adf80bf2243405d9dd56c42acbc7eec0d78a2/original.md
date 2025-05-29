```
XPRSwritesol(prob, filename, flags)::prob
```

Writes the current solution to a CSV format ASCII file, problem_name`.asc` (and `.hdr`).

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `filename::Union{Nothing,AbstractString}`: A string of up to MAXPROBNAMELENGTH characters containing the file name to which the solution is to be written.
  * `flags::Union{Nothing,AbstractString}`: Flags to control which optional fields are output: ssequence number; nname; ttype; bbasis status; aactivity; ccost (columns), slack (rows); llower bound; uupper bound; ddj (column; reduced costs), dual value (rows; shadow prices); rright hand side (rows).If no flags are specified, all fields are output.Additional flags: poutputs in full precision; qonly outputs vectors with nonzero optimum value; xoutput the current LP solution instead of the MIP solution; zcompress the output file.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSwritesol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSwritesol.html) in the C API.
