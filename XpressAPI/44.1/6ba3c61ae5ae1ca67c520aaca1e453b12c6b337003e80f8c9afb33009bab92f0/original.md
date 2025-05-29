```
XPRSnlpgetformulastr(prob, row, maxbytes)::formula, nbytes
```

Retrieve a single matrix formula in a character string.

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `row::Integer`: Integer holding the row index for the formula.
  * `maxbytes::Integer`: Length of the `formula` buffer.

# Return values

  * `formula::AbstractString`: Character buffer in which the formula will be placed in the same format as used for input from a file.
  * `nbytes::Int32`: Will be set to the length of the formula, not including the null terminator.

See also the documentation of the correponding function [XPRSnlpgetformulastr](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpgetformulastr.html) in the C API.
