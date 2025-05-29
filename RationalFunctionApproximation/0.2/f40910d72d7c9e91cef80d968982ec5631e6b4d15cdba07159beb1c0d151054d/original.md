```
get_history(r::Approximation)
```

Parse the convergence history of a rational approximation.

# Arguments

  * `r::Approximation`: the approximation to get the history from

# Returns

  * `::Vector`: degrees of the approximations
  * `::Vector`: estimated maximum errors of the approximations
  * `::Vector{Vector}`: poles of the approximations
  * `::Vector{Vector}`: allowed poles of the approximations
  * `::Integer`: index of the best approximation

See also [`convergenceplot`](@ref).
