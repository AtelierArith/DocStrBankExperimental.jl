```
XPRSnlpevaluateformula(prob, parsed, type, values)::value
```

Evaluate a formula using the current values of the variables

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `parsed::Integer`: integer indicating whether the formula of the item is in internal unparsed format (`parsed`=0) or parsed (reverse Polish) format (`parsed`=1).
  * `type::AbstractVector{Integer}`: Integer array of token types for the formula.
  * `values::AbstractVector{Number}`: Double array of values corresponding to `type`.

# Return value

  * `value::Float64`: Address of a double precision value to receive the result of the calculation.

See also the documentation of the correponding function [XPRSnlpevaluateformula](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpevaluateformula.html) in the C API.
