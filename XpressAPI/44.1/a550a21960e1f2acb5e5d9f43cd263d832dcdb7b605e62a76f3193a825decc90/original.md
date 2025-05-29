```
XPRSsetlogfile(prob, filename)::prob
```

This directs all Optimizer output to a log file.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `filename::Union{Nothing,AbstractString}`: A string of up to MAXPROBNAMELENGTH characters containing the file name to which all logging output should be written.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSsetlogfile](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsetlogfile.html) in the C API.
