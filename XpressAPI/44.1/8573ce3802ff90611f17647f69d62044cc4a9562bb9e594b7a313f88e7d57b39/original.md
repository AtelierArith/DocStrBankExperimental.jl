```
XPRSgetnamelist(prob, type, first, last)::names
```

Returns the names for the rows, columns, sets, piecewise linear constraints, general constraints or objectives in a given range.

The names will be returned in a character buffer, with no trailing whitespace and with each name being separated by a nothing character.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `type::Integer`: XPRS*NAMES*ROW`(=1)` if row names are required; XPRS*NAMES*COLUMN`(=2)` if column names are required; XPRS*NAMES*SET`(=3)` if set names are required; XPRS*NAMES*PWLCONS`(=4)` if piecewise linear constraint names are required; XPRS*NAMES*GENCONS`(=5)` if general constraint names are required; XPRS*NAMES*OBJECTIVE`(=6)` if objective function names are required.
  * `first::Integer`: First row, column, set, piecewise linear or general constraint in the range.
  * `last::Integer`: Last row, column, set, piecewise linear or general constraint in the range.

# Return value

  * `names::AbstractVector{AbstractString}`: A buffer into which the names will be returned as a sequence of null-terminated strings.

See also the documentation of the correponding function [XPRSgetnamelist](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetnamelist.html) in the C API.
