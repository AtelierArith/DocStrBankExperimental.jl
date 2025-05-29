```
BVPSOL(; bvpclass = 2, sol_method = 0, odesolver = nothing)
BVPSOL(bvpclass::Int, sol_methods::Int, odesolver)
```

A FORTRAN77 code which solves highly nonlinear **two point boundary value problems** using a local linear solver (condensing algorithm) or a global sparse linear solver for the solution of the arising linear subproblems, by Peter Deuflhard, Georg Bader, Lutz Weimann. For detailed documentation, see [ODEInterface.jl](https://github.com/luchr/ODEInterface.jl/blob/master/doc/SolverOptions.md#bvpsol).

## Keyword Arguments

```
- `bvpclass`: Boundary value problem classification, default as highly nonlinear with
  bad initial data, available choices:
    - `0`: Linear boundary value problem.
    - `1`: Nonlinear with good initial data.
    - `2`: Highly Nonlinear with bad initial data.
    - `3`: Highly nonlinear with bad initial data and initial rank reduction to
      seperable linear boundary conditions.
- `sol_method`: Switch for solution methods, default as local linear solver with
  condensing algorithm, available choices:
    - `0`: Use local linear solver with condensing algorithm.
    - `1`: Use global sparse linear solver.
- `odesolver`: Either `nothing` or ode-solver(dopri5, dop853, seulex, etc.).
```

!!! note
    Only available if the `ODEInterface` package is loaded.

