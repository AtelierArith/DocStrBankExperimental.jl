```
XPRSstrongbranch(prob, nbounds, colind, bndtype, bndval, iterlim, objval, status)::objval, status
```

Performs strong branching iterations on all specified bound changes.

For each candidate bound change, `XPRSstrongbranch` performs dual simplex iterations starting from the current optimal solution of the base LP, and returns both the status and objective value reached after these iterations.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `nbounds::Integer`: Number of bound changes to try.
  * `colind::AbstractVector{Integer}`: Integer array of size `nbounds` containing the indices of the columns on which the bounds will change.
  * `bndtype::AbstractVector{Cchar}`: Character array of length `nbounds` indicating the type of bound to change: Uindicates change the upper bound; Lindicates change the lower bound; Bindicates change both bounds, i.e. fix the column.
  * `bndval::AbstractVector{Number}`: Double array of length `nbounds` giving the new bound values.
  * `iterlim::Integer`: Maximum number of LP iterations to perform for each bound change.
  * `objval::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Objective value of each LP after performing the strong branching iterations. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `status::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Status of each LP after performing the strong branching iterations, as detailed for the LPSTATUS attribute. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `objval::Union{Nothing,AbstractVector{Float64}}`: Objective value of each LP after performing the strong branching iterations.
  * `status::Union{Nothing,AbstractVector{Int32}}`: Status of each LP after performing the strong branching iterations, as detailed for the LPSTATUS attribute.

See also the documentation of the correponding function [XPRSstrongbranch](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSstrongbranch.html) in the C API.
