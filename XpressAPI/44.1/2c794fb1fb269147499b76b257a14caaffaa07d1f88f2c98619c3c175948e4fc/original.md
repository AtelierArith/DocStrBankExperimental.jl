```
XPRSaddgencons64(prob, ncons, ncols, nvals, contype, resultant, colstart, colind, valstart, val)::prob
```

Adds one or more general constraints to the problem.

Each general constraint `y = f(x1, ..., xn, c1, ..., cn)` consists of one or more (input) columns xi, zero or more constant values ci and a resultant (output column) y, different from all xi. General constraints include `maximum` and `minimum` (arbitrary number of input columns of any type and arbitrary number of input values, at least one total), `and` and `or` (at least one binary input column, no constant values, binary resultant) and `absolute value` (exactly one input column of arbitrary type, no constant values).

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `ncons::Integer`: The number of general constraints to add.
  * `ncols::Integer`: The total number of input variables in general constraints that should be added.
  * `nvals::Integer`: The total number of constant values in general constraints that should be added.
  * `contype::AbstractVector{XPRSGenConsType}`: Integer array of length `ncons` containing the types of the general constraints: XPRS*GENCONS*MAX (0)indicates a `maximum` constraint; XPRS*GENCONS*MIN (1)indicates a `minimum` constraint; XPRS*GENCONS*AND (2)indicates an `and` constraint.
  * `resultant::AbstractVector{Integer}`: Integer array of length `ncons` containing the indices of the output variables of the general constraints.
  * `colstart::AbstractVector{Integer}`: Integer array of length `ncons` containing the start index of each general constraint in the `colind` array.
  * `colind::AbstractVector{Integer}`: Integer array of length `ncols` containing the input variables in all general constraints.
  * `valstart::AbstractVector{Integer}`: Integer array of length `ncons` containing the start index of each general constraint in the `val` array (may be `nothing` if `ncoefs = 0`).
  * `val::AbstractVector{Number}`: Double array of length `nvals` containing the constant values in all general constraints (may be `nothing` if `ncoefs = 0`).

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSaddgencons64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSaddgencons64.html) in the C API.
