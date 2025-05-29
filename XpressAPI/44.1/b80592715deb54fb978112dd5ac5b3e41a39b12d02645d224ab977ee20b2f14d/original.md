```
XPRSnlpgetformulastring(prob, row, maxbytes)::formula
```

**Deprecated**Use XPRSnlpgetformulastr instead.

Retrieve a single matrix formula in a character string.

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `row::Integer`: Integer holding the row index for the formula.
  * `maxbytes::Integer`: Maximum length of returned formula.

# Return value

  * `formula::AbstractString`: Character buffer in which the formula will be placed in the same format as used for input from a file.

See also the documentation of the correponding function [XPRSnlpgetformulastring](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpgetformulastring.html) in the C API.
