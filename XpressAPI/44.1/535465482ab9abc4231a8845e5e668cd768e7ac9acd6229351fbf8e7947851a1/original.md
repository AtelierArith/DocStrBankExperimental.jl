```
XPRSdelsets(prob, nsets, setind)::prob
```

Delete sets from a problem.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `nsets::Integer`: Number of sets to delete.
  * `setind::AbstractVector{Integer}`: An integer array of length `nsets` containing the sets to delete.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSdelsets](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSdelsets.html) in the C API.
