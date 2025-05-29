```
XPRSslpchgcoef(prob, row, col, factor, parsed, type, value)::prob
```

Add or change a single matrix coefficient using a parsed or unparsed formula.

For a simpler version of this function see XSLPchgformula.

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `row::Integer`: The index of the matrix row for the coefficient.
  * `col::Integer`: The index of the matrix column for the coefficient.
  * `factor::Union{Nothing,Float64}`: Address of a double precision variable holding the constant multiplier for the formula.
  * `parsed::Integer`: Integer indicating the whether the token arrays are formatted as internal unparsed (`parsed`=0) or internal parsed reverse Polish (`parsed`=1).
  * `type::AbstractVector{Integer}`: Array of token types providing the description and formula for each item.
  * `value::AbstractVector{Number}`: Array of values corresponding to the types in `type`.

# Return value

  * `prob::XPRSprob`: The current SLP problem.

See also the documentation of the correponding function [XPRSslpchgcoef](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpchgcoef.html) in the C API.
