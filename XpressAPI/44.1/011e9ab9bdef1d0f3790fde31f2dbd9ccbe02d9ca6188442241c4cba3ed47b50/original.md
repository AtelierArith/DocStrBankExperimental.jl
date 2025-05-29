```
XPRSnlpchgformulastr(prob, row, formula)::prob
```

Add or replace a single matrix formula using a character string for the formula.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `row::Integer`: The index of the matrix row for the coefficient.
  * `formula::Union{Nothing,AbstractString}`: Character string holding the formula with the tokens separated by spaces.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSnlpchgformulastr](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpchgformulastr.html) in the C API.
