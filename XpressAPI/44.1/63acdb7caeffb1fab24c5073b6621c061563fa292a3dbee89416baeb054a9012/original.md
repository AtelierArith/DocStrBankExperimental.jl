```
XPRSslpaddcoefs(prob, ncoefs, rowind, colind, factor, formulastart, parsed, type, value)::prob
```

Add non-linear coefficients to the SLP problem.

For a simpler version of this function see XSLPaddformulas.

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `ncoefs::Integer`: Number of non-linear coefficients to be added.
  * `rowind::AbstractVector{Integer}`: Integer array holding index of row for the coefficient.
  * `colind::AbstractVector{Integer}`: Integer array holding index of column for the coefficient.
  * `factor::AbstractVector{Number}`: Double array holding factor by which formula is scaled.
  * `formulastart::AbstractVector{Integer}`: Integer array of length `ncoefs+1` holding the start position in the arrays `type` and `value` of the formula for the coefficients.
  * `parsed::Integer`: Integer indicating whether the token arrays are formatted as internal unparsed (`parsed`=0) or internal parsed reverse Polish (`parsed`=1).
  * `type::AbstractVector{Integer}`: Array of token types providing the formula for each coefficient.
  * `value::AbstractVector{Number}`: Array of values corresponding to the types in `type`.

# Return value

  * `prob::XPRSprob`: The current SLP problem.

See also the documentation of the correponding function [XPRSslpaddcoefs](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpaddcoefs.html) in the C API.
