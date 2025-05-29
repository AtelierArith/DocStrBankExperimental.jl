```
XPRSnlpchgformulastring(prob, row, formula)::prob
```

**Deprecated**Use XPRSnlpchgformulastr instead.

Add or replace a single matrix formula using a character string for the formula.

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `row::Integer`: The index of the matrix row for the coefficient.
  * `formula::Union{Nothing,AbstractString}`: Character string holding the formula with the tokens separated by spaces.

# Return value

  * `prob::XPRSprob`: The current SLP problem.

See also the documentation of the correponding function [XPRSnlpchgformulastring](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpchgformulastring.html) in the C API.
