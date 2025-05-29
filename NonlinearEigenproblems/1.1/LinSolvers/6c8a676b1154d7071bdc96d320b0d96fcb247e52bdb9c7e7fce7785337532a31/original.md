```
FactorizeLinSolverCreator(;umfpack_refinements,max_factorizations,nep,precomp_values)
```

`FactorizeLinSolverCreator`-objects can instantiate `FactorizeLinSolver` objects via the `create_linsolver` function.

The `FactorizeLinSolver` is based on `factorize`-calls. The time point of the call to `factorize` can be controlled by parameters to `FactorizeLinSolverCreator`:

  * By default, the `factorize` call is carried out by the instantiation of the `FactorizeLinSolver`, i.e., when the NEP-solver calls `create_linsolver`.
  * You can also precompute the factorization, at the time point when you instantiate `FactorizeLinSolverCreator`. If you set `precomp_values::Vector{Number}` to a non-empty vector, and set `nep` kwarg, the factorization (of all λ-values in the `precomp_values`) will be computed  when the `FactorizeLinSolverCreator` is instantiated. If the NEP-solver calls a `create_linsolver` with a λ-value from that vector, the factorization will be used (otherwise it will be computed).

Further recycling is possible. If the variable `max_factorizations` is set to a positive value, the object will store that many factorizations for possible reuse. Every `lin_solve`-call then computes a factorization, unless a `lin_solve`-call for that `λ` has been computed earlier. This procedure can at most store `max_factorization` (which can be set `Inf`).

See also: [`FactorizeLinSolver`](@ref), [`create_linsolver`](@ref)
