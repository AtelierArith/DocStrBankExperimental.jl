```
XPRSreaddirs(prob, filename)::prob
```

Reads a directives file to help direct the tree search.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `filename::Union{Nothing,AbstractString}`: A string of up to MAXPROBNAMELENGTH characters containing the file name from which the directives are to be read.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSreaddirs](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSreaddirs.html) in the C API.
