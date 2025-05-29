```
XPRSclearrowflags(prob, flags, first, last)::prob
```

Clears extra information attached to a range of rows.

# Arguments

  * `prob::XPRSprob`: The current problem
  * `flags::AbstractVector{Integer}`: Int array of length `last-first+1` including type of extra information to remove (see below)
  * `first::Integer`: First row index to be checked
  * `last::Integer`: Last row index to be checked

# Return value

  * `prob::XPRSprob`: The current problem

See also the documentation of the correponding function [XPRSclearrowflags](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSclearrowflags.html) in the C API.
