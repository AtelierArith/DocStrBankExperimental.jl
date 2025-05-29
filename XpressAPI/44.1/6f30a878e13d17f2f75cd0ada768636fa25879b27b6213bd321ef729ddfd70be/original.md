```
XPRSslpchgrowstatus(prob, row)::status
```

Change the status setting of a constraint

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `row::Integer`: The index of the matrix row to be changed.

# Return value

  * `status::Int32`: Address of an integer holding a bitmap with the new status settings.

See also the documentation of the correponding function [XPRSslpchgrowstatus](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpchgrowstatus.html) in the C API.
