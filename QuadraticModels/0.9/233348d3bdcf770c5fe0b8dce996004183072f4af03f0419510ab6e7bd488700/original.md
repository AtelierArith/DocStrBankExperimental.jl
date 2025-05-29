```
stats_ps = presolve(qm::QuadraticModel{T, S}; fixed_vars_only = false, kwargs...)
```

Apply a presolve routine to `qm` and returns a  [`GenericExecutionStats`](https://juliasmoothoptimizers.github.io/SolverCore.jl/stable/reference/#SolverCore.GenericExecutionStats) from the package [`SolverCore.jl`](https://github.com/JuliaSmoothOptimizers/SolverCore.jl). The presolve operations currently implemented are:

  * remove empty rows
  * remove singleton rows
  * fix linearly unconstrained variables (lps)
  * remove free linear singleton columns whose associated variable does not appear in the hessian
  * remove fixed variables

The `PresolvedQuadraticModel{T, S} <: AbstractQuadraticModel{T, S}` is located in the `solver_specific` field:

```
psqm = stats_ps.solver_specific[:presolvedQM]
```

and should be used to call [`postsolve`](@ref). Use `fixed_vars_only = true` if you only want to remove fixed variables. Maximization problems are transformed to minimization problems. If you need the objective of a presolved maximization problem, make sure to take the opposite of the objective of the presolved problem.

If the presolved problem has 0 variables, `stats_ps.solution` contains a solution of the primal problem, `stats_ps.multipliers` is a zero `SparseVector`, and, if we define

```
s = qm.data.c + qm.data.H * stats_ps.solution
```

`stats_ps.multipliers_L` is the positive part of `s` and `stats_ps.multipliers_U` is the opposite of the negative part of `s`. The presolve operations are inspired from [`MathOptPresolve.jl`](https://github.com/mtanneau/MathOptPresolve.jl), and from:

  * Gould, N., Toint, P. [*Preprocessing for quadratic programming*](https://doi.org/10.1007/s10107-003-0487-2), Math. Program., Ser. B 100, 95–132 (2004).
