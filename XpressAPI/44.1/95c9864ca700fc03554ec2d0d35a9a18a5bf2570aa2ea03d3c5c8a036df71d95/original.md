```
XPRSgetmipentities(prob, coltype, colind, limit, settype, start, setcols, refval)::nentities, nsets, coltype, colind, limit, settype, start, setcols, refval
```

Retrieves integr and entity information about a problem.

It must be called before XPRSmipoptimize if the presolve option is used.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `coltype::Union{XPRSallocatable,Nothing,AbstractVector{Cchar}}`: Character array of length `nentities` where the entity types will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `colind::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array of length `nentities` where the column indices of the MIP entities will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `limit::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `nentities` where the limits for the partial integer variables and lower bounds for the semi-continuous and semi-continuous integer variables will be returned (any entries in the positions corresponding to binary and integer variables will be meaningless). You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `settype::Union{XPRSallocatable,Nothing,AbstractVector{Cchar}}`: Character array of length `nsets` where the set types will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `start::AbstractVector{Int32}`: Integer array where the offsets into the `setcols` and `refval` arrays indicating the start of the sets will be returned.
  * `setcols::AbstractVector{Int32}`: Integer array of length `SETMEMBERS` where the columns in each set will be returned.
  * `refval::AbstractVector{Float64}`: Double array of length `SETMEMBERS` where the reference row entries for each member of the sets will be returned.

# Return values

  * `nentities::Int32`: Pointer to the integer where the number of binary, integer, semi-continuous, semi-continuous integer and partial integer entities will be returned.
  * `nsets::Int32`: Pointer to the integer where the number of SOS1 and SOS2 sets will be returned.
  * `coltype::Union{Nothing,AbstractVector{Cchar}}`: Character array of length `nentities` where the entity types will be returned.
  * `colind::Union{Nothing,AbstractVector{Int32}}`: Integer array of length `nentities` where the column indices of the MIP entities will be returned.
  * `limit::Union{Nothing,AbstractVector{Float64}}`: Double array of length `nentities` where the limits for the partial integer variables and lower bounds for the semi-continuous and semi-continuous integer variables will be returned (any entries in the positions corresponding to binary and integer variables will be meaningless).
  * `settype::Union{Nothing,AbstractVector{Cchar}}`: Character array of length `nsets` where the set types will be returned.
  * `start::AbstractVector{Int32}`: Integer array where the offsets into the `setcols` and `refval` arrays indicating the start of the sets will be returned.
  * `setcols::AbstractVector{Int32}`: Integer array of length `SETMEMBERS` where the columns in each set will be returned.
  * `refval::AbstractVector{Float64}`: Double array of length `SETMEMBERS` where the reference row entries for each member of the sets will be returned.

See also the documentation of the correponding function [XPRSgetmipentities](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetmipentities.html) in the C API.
