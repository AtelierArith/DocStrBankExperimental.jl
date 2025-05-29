```
XPRSrefinemipsol(prob, options, flags, solution, refined)::refined, status
```

**Deprecated**Please use REFINEOPS instead.

Executes the MIP solution refiner.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `options::Integer`: Refinement options: 0Reducing MIP fractionality is priority (If bit 10 of REFINEOPS is set, will switch to other mode if unsuccessful).
  * `flags::Union{Nothing,AbstractString}`: Flags passed to any optimization calls during refinement.
  * `solution::AbstractVector{Number}`: The MIP solution to refine.
  * `refined::Union{XPRSallocatable,AbstractVector{Float64}}`: The refined MIP solution in case of success You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.

# Return values

  * `refined::AbstractVector{Float64}`: The refined MIP solution in case of success
  * `status::Int32`: Refinement results: 0An error has occurred 1The solution has been refined 2Current solution meets target criteria 3Solution cannot be refined 5The solution has been refined, but MIP fractionality could not be reduced.

See also the documentation of the correponding function [XPRSrefinemipsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSrefinemipsol.html) in the C API.
