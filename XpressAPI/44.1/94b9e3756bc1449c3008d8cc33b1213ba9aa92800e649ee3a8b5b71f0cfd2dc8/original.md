```
XPRSslpchgrowwt(prob, row, weight)::prob
```

Set or change the initial penalty error weight for a row

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `row::Integer`: The index of the row whose weight is to be set or changed.
  * `weight::Union{Nothing,Float64}`: Address of a double precision variable holding the new value of the weight.

# Return value

  * `prob::XPRSprob`: The current SLP problem.

See also the documentation of the correponding function [XPRSslpchgrowwt](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpchgrowwt.html) in the C API.
