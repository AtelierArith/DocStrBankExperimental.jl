```
XPRSslpchgdeltatype(prob, nvars, varind, deltatypes, values)::prob
```

Changes the type of the delta assigned to a nonlinear variable

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `nvars::Integer`: The number of SLP variables to change the delta type for.
  * `varind::AbstractVector{Integer}`: Indices of the variables to change the deltas for.
  * `deltatypes::AbstractVector{Integer}`: Type if the delta variable: 0Differentiable variable, default.
  * `values::AbstractVector{Number}`: Grid or minimum step sizes for the variables.

# Return value

  * `prob::XPRSprob`: The current SLP problem.

See also the documentation of the correponding function [XPRSslpchgdeltatype](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpchgdeltatype.html) in the C API.
