```
dci(nlp; kwargs...)
dci(nlp, x; kwargs...)
dci(nlp, meta, x)
```

Compute a local minimum of an equality-constrained optimization problem using DCI algorithm from Bielschowsky & Gomes (2008).

# Arguments

  * `nlp::AbstractNLPModel`: the model solved, see `NLPModels.jl`.
  * `x`: Initial guess. If `x` is not specified, then `nlp.meta.x0` is used.
  * `meta`: The keyword arguments are used to initialize a [`MetaDCI`](@ref).

For advanced usage, the principal call to the solver uses a [`DCIWorkspace`](@ref).

```
solve!(workspace, nlp)
solve!(workspace, nlp, stats)
```

# Output

The returned value is a `GenericExecutionStats`, see `SolverCore.jl`.

# Callback

The callback is called at each iteration. The expected signature of the callback is `callback(nlp, workspace, stats)`, and its output is ignored. Changing any of the input arguments will affect the subsequent iterations. In particular, setting `stats.status = :user` will stop the algorithm. All relevant information should be available in `nlp` and `workspace`. Notably, you can access, and modify, the following:

  * `workspace`: current workspace;
  * `stats`: structure holding the output of the algorithm (`GenericExecutionStats`), which contains, among other things:

      * `stats.dual_feas`: norm of current gradient;
      * `stats.iter`: current iteration counter;
      * `stats.objective`: current objective function value;
      * `stats.status`: current status of the algorithm. Should be `:unknown` unless the algorithm has attained a stopping criterion. Changing this to anything will stop the algorithm, but you should use `:user` to properly indicate the intention.
      * `stats.elapsed_time`: elapsed time in seconds.

# References

This method implements the Dynamic Control of Infeasibility for equality-constrained problems described in

```
Dynamic Control of Infeasibility in Equality Constrained Optimization
Roberto H. Bielschowsky and Francisco A. M. Gomes
SIAM J. Optim., 19(3), 2008, 1299–1325.
https://doi.org/10.1137/070679557
```

# Examples

```jldoctest; output = false
using ADNLPModels, DCISolver
nlp = ADNLPModel(x -> 100 * (x[2] - x[1]^2)^2 + (x[1] - 1)^2, [-1.2; 1.0])
stats = dci(nlp, verbose = 0)
stats

# output

"Execution stats: first-order stationary"
```
