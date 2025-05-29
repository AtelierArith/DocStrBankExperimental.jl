```
guesswork_upper_bound(
    p::AbstractVector{T},
    ρBs::AbstractVector{<:AbstractMatrix};
    make_solver,
    c::AbstractVector = T.(1:length(p)),
    max_retries = 50,
    max_time = Inf,
    num_constraints = Inf,
    verbose::Bool = false,
    num_steps_per_SA_run::Integer = length(p)^2 * 500,
) where {T<:Number} -> NamedTuple
```

Computes an upper bound to the guesswork problem associated to the c-q state specified by `p` and `ρBs`, as in [`guesswork`](@ref). A custom cost vector `c` may be optionally passed. If the keyword argument `verbose` is set to true, information is printed about each iteration of the algorithm.

The keyword argument `make_solver` is required, and must pass a *function that creates a solver instances*. For example, instead of passing `SCSSolver()`, pass `() -> SCSSolver()`. This is needed because the algorithm used in `guesswork_upper_bound` solves a sequence of SDPs, not just one.

The algorithm has three termination criteria which are controlled by keyword arguments. The algorithm stops when any of the following occur:

  * `max_retries` simulated annealing attempts fail to find a violated constraint.
  * `num_constraints` constraints have been added to the dual SDP
  * The total runtime of the algorithm is projected to exceed `max_time` on the next iteration.

By default, `max_retries` is set to 50, while `num_constraints` and `max_time` are set to infinity.

Lastly, the keyword argument `num_steps_per_SA_run` controls the runtime of the simulated annealing algorithm. Increase `num_steps_per_SA_run` to search longer for a violated constraint within a given simulated annealing run.
