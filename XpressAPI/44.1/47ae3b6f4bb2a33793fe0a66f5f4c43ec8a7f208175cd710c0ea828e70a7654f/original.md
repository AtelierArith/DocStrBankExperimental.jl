```
XPRSgetpivots(prob, enter, outlist, x, maxpivots)::outlist, x, objval, npivots
```

Returns a list of potential leaving variables if a specified variable enters the basis.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `enter::Integer`: Index of the specified row or column to enter basis.
  * `outlist::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array of length at least `maxpivots` to hold list of potential leaving variables. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `x::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length ROWS`+`SPAREROWS`+`COLS to hold the values of all the variables that would result if `enter` entered the basis. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `maxpivots::Integer`: Maximum number of potential leaving variables to return.

# Return values

  * `outlist::Union{Nothing,AbstractVector{Int32}}`: Integer array of length at least `maxpivots` to hold list of potential leaving variables.
  * `x::Union{Nothing,AbstractVector{Float64}}`: Double array of length ROWS`+`SPAREROWS`+`COLS to hold the values of all the variables that would result if `enter` entered the basis.
  * `objval::Float64`: Pointer to a double where the objective function value that would result if `enter` entered the basis will be returned.
  * `npivots::Int32`: Pointer to an integer where the actual number of potential leaving variables will be returned.

See also the documentation of the correponding function [XPRSgetpivots](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetpivots.html) in the C API.
