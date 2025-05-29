```
MCSBlackBoxOptim(; kwargs...)
```

The black box derivative-free optimization algorithm used in [`minimal_critical_shock`](@ref).

## Keyword arguments

  * `guess = nothing`: a initial guess for the minimal critical shock given to the optimization algorithm. If not `nothing`, `random_algo` below is ignored.
  * `max_steps = 10000`: maximum number of steps for the optimization algorithm.
  * `penalty = 1000.0`: penalty value for the objective function for perturbations that do not lead to a different basin of attraction. This value is added to the norm of the perturbation and its value should be much larger than the typical sizes of the basins of attraction.
  * `print_info`: boolean value, if true, the optimization algorithm will print information on the evaluation steps of objective function, `default = false`.
  * `random_algo = MCSBruteForce(100, 100, 0.99)`: an instance of [`MCSBruteForce`](@ref) that can be used to provide an initial guess.
  * `bbkwargs = NamedTuple()`: additional keyword arguments propagated to `BlackBoxOptim.bboptimize` for selecting solver, accuracy, and more.

## Description

The algorithm uses BlackBoxOptim.jl and a penalized objective function to minimize. y function used as a constraint function. So, if we hit another basin during the search we encourage the algorithm otherwise we punish it with some penalty. The function to minimize is (besides some details):

```julia
function mfs_objective(perturbation, u0, mapper, penalty)
    dist = norm(perturbation)
    if mapper(u0 + perturbation) == mapper(u0)
        # penalize if we stay in the same basin:
        return dist + penalty
    else
        return dist
    end
end
```

Using an initial guess can be beneficial to both performance and accuracy, which is why the output of a crude [`MCSBruteForce`](@ref) is used to provide a guess. This can be disabled by either passing a `guess` vector explicitly or by giving `nothing` as `random_algo`.
