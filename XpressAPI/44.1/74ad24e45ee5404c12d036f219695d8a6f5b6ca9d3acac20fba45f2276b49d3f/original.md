```
XPRSaddnames(prob, type, names, first, last)::prob
```

When a model is loaded, the rows, columns, sets, piecewise linear and general constraints of the model may not have names associated with them.

This may not be important as the rows, columns, sets, piecewise linear and general constraints can be referred to by their sequence numbers. However, if you wish row, column, set, piecewise linear and general constraint names to appear in the ASCII solutions files, the names for a range of rows/columns/... can be added with `XPRSaddnames`.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `type::Integer`: XPRS*NAMES*ROW`(=1)` for row names; XPRS*NAMES*COLUMN`(=2)` for column names; XPRS*NAMES*SET`(=3)` for set names; XPRS*NAMES*PWLCONS`(=4)` for piecewise linear constraint names; XPRS*NAMES*GENCONS`(=5)` for general constraint names; XPRS*NAMES*OBJECTIVE`(=6)` for objective names.
  * `names::AbstractVector{AbstractString}`: Character buffer containing the null-terminated string names.
  * `first::Integer`: Start of the range of rows, columns, sets, piecewise linear constraints, general constraints or objectives.
  * `last::Integer`: End of the range of rows, columns, sets, piecewise linear constraints, general constraints or objectives.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSaddnames](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSaddnames.html) in the C API.
