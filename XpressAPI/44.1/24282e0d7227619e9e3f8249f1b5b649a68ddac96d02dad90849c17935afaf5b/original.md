```
XPRSgetindicators(prob, colind, complement, first, last)::colind, complement
```

Returns the indicator constraint condition (indicator variable and complement flag) associated to the rows in a given range.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `colind::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array of length `last-first+1` where the column indices of the indicator variables are to be placed. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `complement::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array of length `last-first+1` where the indicator complement flags will be returned: 0not an indicator constraint (in this case the corresponding entry in the `colind` array is ignored); 1for indicator constraints with condition "`bin = 1`"; -1for indicator constraints with condition "`bin = 0`". You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `first::Integer`: First row in the range.
  * `last::Integer`: Last row in the range (inclusive).

# Return values

  * `colind::Union{Nothing,AbstractVector{Int32}}`: Integer array of length `last-first+1` where the column indices of the indicator variables are to be placed.
  * `complement::Union{Nothing,AbstractVector{Int32}}`: Integer array of length `last-first+1` where the indicator complement flags will be returned: 0not an indicator constraint (in this case the corresponding entry in the `colind` array is ignored); 1for indicator constraints with condition "`bin = 1`"; -1for indicator constraints with condition "`bin = 0`".

See also the documentation of the correponding function [XPRSgetindicators](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetindicators.html) in the C API.
