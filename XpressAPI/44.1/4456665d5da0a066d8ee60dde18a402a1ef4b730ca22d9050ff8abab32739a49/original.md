```
XPRSchgcoltype(prob, ncols, colind, coltype)::prob
```

Used to change the type of a specified set of columns in the matrix.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `ncols::Integer`: Number of columns to change.
  * `colind::AbstractVector{Integer}`: Integer array of length `ncols` containing the indices of the columns.
  * `coltype::AbstractVector{Cchar}`: Character array of length `ncols` giving the new column types: Cindicates a continuous column; Bindicates a binary column; Iindicates an integer column.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSchgcoltype](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgcoltype.html) in the C API.
