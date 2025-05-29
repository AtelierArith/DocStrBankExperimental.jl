```
XPRSslpchgccoef(prob, row, col, factor, formula)::prob
```

**Deprecated**Use XPRSslpchgcoefstr instead.

Add or change a single matrix coefficient using a character string for the formula. For a simpler version of this function see XPRSnlpchgformulastr.

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `row::Integer`: The index of the matrix row for the coefficient.
  * `col::Integer`: The index of the matrix column for the coefficient.
  * `factor::Union{Nothing,Float64}`: Address of a double precision variable holding the constant multiplier for the formula.
  * `formula::Union{Nothing,AbstractString}`: Character string holding the formula with the tokens separated by spaces.

# Return value

  * `prob::XPRSprob`: The current SLP problem.

See also the documentation of the correponding function [XPRSslpchgccoef](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpchgccoef.html) in the C API.
