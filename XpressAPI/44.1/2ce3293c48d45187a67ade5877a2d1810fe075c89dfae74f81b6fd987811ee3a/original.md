```
XPRS_bo_getrows(bo, branch, maxrows, maxcoefs, rowtype, rhs, start, colind, rowcoef)::nrows, ncoefs, rowtype, rhs, start, colind, rowcoef
```

Returns the constraints for a branch of a user branching object.

# Arguments

  * `bo::XPRSbranchobject`: The user branching object to inspect.
  * `branch::Integer`: The number of the branch to get the constraints from.
  * `maxrows::Integer`: Maximum number of rows to return.
  * `maxcoefs::Integer`: Maximum number of non zero coefficients to return.
  * `rowtype::Union{XPRSallocatable,Nothing,AbstractVector{Cchar}}`: Character array of length `maxrows` where the types of the rows will be returned: LLess than type. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `rhs::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `maxrows` where the right hand side values will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `start::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array of length `maxrows` which will be filled with the offsets of the `colind` and `rowcoef` arrays of the start of the non zero coefficients in the returned constraints. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `colind::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array of length `maxcoefs` which will be filled with the column indices for the non zero coefficients. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `rowcoef::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `maxcoefs` which will be filled with the non zero coefficient values. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `nrows::Int32`: Memory location where the number of rows should be returned.
  * `ncoefs::Int32`: Memory location where the number of non zero coefficients in the constraints should be returned.
  * `rowtype::Union{Nothing,AbstractVector{Cchar}}`: Character array of length `maxrows` where the types of the rows will be returned: LLess than type.
  * `rhs::Union{Nothing,AbstractVector{Float64}}`: Double array of length `maxrows` where the right hand side values will be returned.
  * `start::Union{Nothing,AbstractVector{Int32}}`: Integer array of length `maxrows` which will be filled with the offsets of the `colind` and `rowcoef` arrays of the start of the non zero coefficients in the returned constraints.
  * `colind::Union{Nothing,AbstractVector{Int32}}`: Integer array of length `maxcoefs` which will be filled with the column indices for the non zero coefficients.
  * `rowcoef::Union{Nothing,AbstractVector{Float64}}`: Double array of length `maxcoefs` which will be filled with the non zero coefficient values.

See also the documentation of the correponding function [XPRS*bo*getrows](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRS_bo_getrows.html) in the C API.
