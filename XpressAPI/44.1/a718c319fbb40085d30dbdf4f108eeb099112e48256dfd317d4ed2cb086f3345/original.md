```
XPRSnlpchgformula(prob, row, parsed, type, value)::prob
```

Add or replace a single matrix formula using a parsed or unparsed formula

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `row::Integer`: The index of the matrix row for the coefficient.
  * `parsed::Integer`: Integer indicating the whether the token arrays are formatted as internal unparsed (`parsed`=0) or internal parsed reverse Polish (`parsed`=1).
  * `type::AbstractVector{Integer}`: Array of token types providing the description and formula for each item.
  * `value::AbstractVector{Number}`: Array of values corresponding to the types in `type`.

# Return value

  * `prob::XPRSprob`: The current SLP problem.

See also the documentation of the correponding function [XPRSnlpchgformula](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpchgformula.html) in the C API.
