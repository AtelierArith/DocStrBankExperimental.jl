```
XPRSgetgencons64(prob, contype, resultant, colstart, colind, maxcols, valstart, val, maxvals, first, last)::contype, resultant, colstart, colind, ncols, valstart, val, nvals
```

Returns the general constraints `y = f(x1, ..., xn, c1, ..., cm)` in a given range.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `contype::Union{XPRSallocatable,Nothing,AbstractVector{XPRSGenConsType}}`: `nothing` if not required or an integer array of length at least `last-first+1` which will be filled with the types of the general constraints: XPRS*GENCONS*MAX (0)indicates a `maximum` constraint; XPRS*GENCONS*MIN (1)indicates a `minimum` constraint; XPRS*GENCONS*AND (2)indicates an `and` constraint. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `resultant::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array which will be filled with the indices of the output variables `y`. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `colstart::Union{XPRSallocatable,Nothing,AbstractVector{Int64}}`: Integer array of length at least `last-first+2` which will be filled with the start index of each general constraint in the `colind` array. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `colind::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array which will be filled with the indices of the input variables `xi`. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `maxcols::Integer`: Maximum number of input columns to be retrieved.
  * `valstart::Union{XPRSallocatable,Nothing,AbstractVector{Int64}}`: Integer array of length at least `last-first+2` which will be filled with the start index of each general constraint in the `val` array. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `val::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Integer array which will be filled with the constant values `ci`. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `maxvals::Integer`: Maximum number of constant values to be retrieved.
  * `first::Integer`: First general constraint in the range.
  * `last::Integer`: Last general constraint in the range.

# Return values

  * `contype::Union{Nothing,AbstractVector{XPRSGenConsType}}`: `nothing` if not required or an integer array of length at least `last-first+1` which will be filled with the types of the general constraints: XPRS*GENCONS*MAX (0)indicates a `maximum` constraint; XPRS*GENCONS*MIN (1)indicates a `minimum` constraint; XPRS*GENCONS*AND (2)indicates an `and` constraint.
  * `resultant::Union{Nothing,AbstractVector{Int32}}`: Integer array which will be filled with the indices of the output variables `y`.
  * `colstart::Union{Nothing,AbstractVector{Int64}}`: Integer array of length at least `last-first+2` which will be filled with the start index of each general constraint in the `colind` array.
  * `colind::Union{Nothing,AbstractVector{Int32}}`: Integer array which will be filled with the indices of the input variables `xi`.
  * `ncols::Int64`: Pointer to return the number of input columns in the `colind` array.
  * `valstart::Union{Nothing,AbstractVector{Int64}}`: Integer array of length at least `last-first+2` which will be filled with the start index of each general constraint in the `val` array.
  * `val::Union{Nothing,AbstractVector{Float64}}`: Integer array which will be filled with the constant values `ci`.
  * `nvals::Int64`: Pointer to return the number of constant values in the `val` array.

See also the documentation of the correponding function [XPRSgetgencons64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetgencons64.html) in the C API.
