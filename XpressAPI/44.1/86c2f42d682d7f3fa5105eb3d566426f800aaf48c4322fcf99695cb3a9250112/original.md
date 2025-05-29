```
XPRSiisisolations(prob, iis)::prob
```

Performs the isolation identification procedure for an Irreducible Infeasible Set (IIS).

This function applies only to linear problems.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `iis::Integer`: The number of the IIS identified by either XPRSiisfirst (IIS), XPRSiisnext (IIS `-n`) or XPRSiisall (IIS `-a`) in which the isolations should be identified.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSiisisolations](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSiisisolations.html) in the C API.
