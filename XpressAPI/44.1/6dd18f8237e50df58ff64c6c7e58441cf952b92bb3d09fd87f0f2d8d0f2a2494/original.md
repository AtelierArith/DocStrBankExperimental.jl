```
XPRSgetcoltype(prob, coltype, first, last)::coltype
```

Returns the column types for the columns in a given range.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `coltype::Union{XPRSallocatable,AbstractVector{Cchar}}`: Character array of length `last-first+1` where the column types will be returned: Cindicates a continuous variable; Iindicates an integer variable; Bindicates a binary variable; Sindicates a semi-continuous variable; Rindicates a semi-continuous integer variable; Pindicates a partial integer variable. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.
  * `first::Integer`: First column in the range.
  * `last::Integer`: Last column in the range.

# Return value

  * `coltype::AbstractVector{Cchar}`: Character array of length `last-first+1` where the column types will be returned: Cindicates a continuous variable; Iindicates an integer variable; Bindicates a binary variable; Sindicates a semi-continuous variable; Rindicates a semi-continuous integer variable; Pindicates a partial integer variable.

See also the documentation of the correponding function [XPRSgetcoltype](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcoltype.html) in the C API.
