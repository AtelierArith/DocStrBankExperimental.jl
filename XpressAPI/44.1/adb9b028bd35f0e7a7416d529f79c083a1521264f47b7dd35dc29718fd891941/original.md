```
XPRSaddsets64(prob, nsets, nelems, settype, start, colind, refval)::prob
```

Allows sets to be added to the problem after passing it to the Optimizer using the input routines.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `nsets::Integer`: Number of new sets.
  * `nelems::Integer`: Number of new nonzeros in the added sets.
  * `settype::AbstractVector{Cchar}`: Character array of length nsets containing the set types: 1indicates a SOS1; 2indicates a SOS2;
  * `start::AbstractVector{Integer}`: Integer array of length `nsets` containing the offsets in the `colind` and `refval` arrays of the start of the elements for each set.
  * `colind::AbstractVector{Integer}`: Integer array of length `nelems` containing the (contiguous) column indices for the elements in each set.
  * `refval::AbstractVector{Number}`: Double array of length `nelems` containing the (contiguous) reference values.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSaddsets64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSaddsets64.html) in the C API.
