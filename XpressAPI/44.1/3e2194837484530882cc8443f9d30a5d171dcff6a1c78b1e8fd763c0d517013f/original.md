```
XPRSpivot(prob, enter, leave)::prob
```

Performs a simplex pivot by bringing variable `enter` into the basis and removing `leave`.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `enter::Integer`: Index of row or column to enter basis.
  * `leave::Integer`: Index of row or column to leave basis.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSpivot](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSpivot.html) in the C API.
