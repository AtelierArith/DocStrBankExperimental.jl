```
Options(;
    x_tol::Real = 1e-8,
    f_tol::Real = 1e-12,
    f_tol_rel::Real = eps(),
    f_tol_abs::Real = 0.0,
    g_tol::Real = 0.0,
    h_tol::Real = 0.0,
    f_calls_limit::Real = 0,
    time_limit::Real = Inf,
    iterations::Int = 1,
    store_convergence::Bool = false,
    debug::Bool = false,
    seed = rand(UInt),
    rng  = default_rng_mh(seed),
    parallel_evaluation = false,
    verbose = false,
)
```

`Options` stores common settings for metaheuristics such as the maximum number of iterations debug options, maximum number of function evaluations, etc.

Main properties:

  * `x_tol` tolerance to the true minimizer if specified in `Information`.
  * `f_tol` tolerance to the true minimum if specified in `Information`.
  * `f_tol_rel` relative tolerance.
  * `f_calls_limit` is the maximum number of function evaluations limit.
  * `time_limit` is the maximum time that `optimize` can spend in seconds.
  * `iterations` is the maximum number of allowed iterations.
  * `store_convergence` if `true`, then push the current `State` in `State.convergence` at each generation/iteration
  * `debug` if `true`, then `optimize` function reports the current `State` (and interest information) for each iterations.
  * `seed` non-negative integer for the random generator seed.
  * `parallel_evaluation` enables batch evaluations.
  * `verbose` show simplified results each iteration.
  * `rng` user-defined Random Number Generator.

# Example

```julia-repl
julia> options = Options(f_calls_limit = 1000, debug=false, seed=1);

julia> f(x) = sum(x.^2)
f (generic function with 1 method)

julia> bounds = [  -10.0 -10 -10; # lower bounds
                    10.0  10 10 ] # upper bounds
2×3 Array{Float64,2}:
 -10.0  -10.0  -10.0
  10.0   10.0   10.0

julia> state = optimize(f, bounds, ECA(options=options));
```
