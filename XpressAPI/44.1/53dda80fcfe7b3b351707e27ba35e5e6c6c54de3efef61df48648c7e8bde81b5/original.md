```
XPRSgetcpcutlist(prob, cuttype, interp, delta, maxcuts, cutind, viol)::ncuts, cutind, viol
```

Returns a list of cut indices from the cut pool.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `cuttype::Integer`: The user defined type of the cuts to be returned.
  * `interp::Integer`: Way in which the cut type is interpreted: -1get all cuts; 1treat cut types as numbers; 2treat cut types as bit maps - get cut if any bit matches any bit set in `cuttype`; 3treat cut types as bit maps - get cut if all bits match those set in `cuttype`.
  * `delta::Float64`: Only those cuts with a signed violation greater than delta will be returned.
  * `maxcuts::Integer`: Maximum number of cuts to be returned.
  * `cutind::Union{XPRSallocatable,Nothing,AbstractVector{Ptr{Cvoid}}}`: Array of length `maxcuts` where the pointers to the cuts will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `viol::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `maxcuts` where the values of the signed violations of the cuts will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `ncuts::Int32`: Pointer to the integer where the number of cuts of type `cuttype` in the cut pool will be returned.
  * `cutind::Union{Nothing,AbstractVector{Ptr{Cvoid}}}`: Array of length `maxcuts` where the pointers to the cuts will be returned.
  * `viol::Union{Nothing,AbstractVector{Float64}}`: Double array of length `maxcuts` where the values of the signed violations of the cuts will be returned.

See also the documentation of the correponding function [XPRSgetcpcutlist](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcpcutlist.html) in the C API.
