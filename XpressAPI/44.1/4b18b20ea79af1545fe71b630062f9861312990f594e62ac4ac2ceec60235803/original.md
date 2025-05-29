```
XPRSgetrowflags(prob, flags, first, last)::flags
```

Retrieve if a range of rows have been set up as special rows.

# Arguments

  * `prob::XPRSprob`: The current problem
  * `flags::Union{XPRSallocatable,AbstractVector{Int32}}`: Int array of length `last-first+1` where type of information (see below) will be returned You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.
  * `first::Integer`: First row index to be checked
  * `last::Integer`: Last row index to be checked

# Return value

  * `flags::AbstractVector{Int32}`: Int array of length `last-first+1` where type of information (see below) will be returned

See also the documentation of the correponding function [XPRSgetrowflags](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetrowflags.html) in the C API.
