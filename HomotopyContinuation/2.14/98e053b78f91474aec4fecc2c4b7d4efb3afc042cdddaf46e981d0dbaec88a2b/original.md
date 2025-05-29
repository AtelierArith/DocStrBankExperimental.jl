```
PathResult
```

A `PathResult` is the result of tracking of a path with [`track`](@ref) using an [`AbstractPathTracker`](@ref) ( e.g. [`EndgameTracker`](@ref))

## Fields

General solution information:

  * `return_code`: See the list of return codes below.
  * `solution::V`: The solution vector.
  * `t::Float64`: The value of `t` at which `solution` was computed. Note that if `return_code` is `:at_infinity`, then `t` is the value when this was decided.
  * `accuracy::Float64`: An estimate the (relative) accuracy of the computed solution.
  * `residual::Float64`: The infinity norm of `H(solution,t)`.
  * `condition_jacobian::Float64`: This is the condition number of the Jacobian at the solution. A high condition number indicates a singular solution or a solution on a positive dimensional component.
  * `singular::Bool`: Whether the solution is considered singular.
  * `winding_number:Union{Nothing, Int}`: The computed winding number. This is a lower bound on the multiplicity of the solution. It is $nothing$ if the Cauchy endgame was not used.
  * `extended_precision::Bool`: Indicate whether extended precision is necessary to achieve the accuracy of the `solution`.
  * `path_number::Union{Nothing,Int}`: The number of the path (optional).
  * `start_solution::Union{Nothing,V}`: The start solution of the path (optional).

Performance information:

  * `accepted_steps::Int`: The number of accepted steps during the path tracking.
  * `rejected_steps::Int`: The number of rejected steps during the path tracking.
  * `extended_precision_used::Bool`: Indicates whether extended precision was necessary to track the path.

Additional path and solution informations

  * `valuation::Vector{Float64}`: An approximation of the valuation of the Puiseux series expansion of $x(t)$.
  * `last_path_point::Tuple{V,Float64}`: The last pair $(x,t)$ before the solution was computed. If the solution was computed with the Cauchy endgame, then the pair $(x,t)$ can be used to rerun the endgame.

## Return codes

Possible return codes are:

  * `:success`: The `EndgameTracker` obtained a solution.
  * `:at_infinity`: The `EndgameTracker` stopped the tracking of the path since it determined that that path is diverging towards infinity.
  * `:at_zero`: The `EndgameTracker` stopped the tracking of the path since it determined that that path has a solution where at least one coordinate is 0. This only happens if the option `zero_is_at_infinity` is `true`.
  * `:excess_solution`: For the solution of the system, the system had to be modified which introduced artificial solutions and this solution is one of them.
  * various return codes indicating termination of the tracking
