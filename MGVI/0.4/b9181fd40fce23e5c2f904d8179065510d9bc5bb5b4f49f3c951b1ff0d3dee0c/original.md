```
struct MVGIConfig
```

MGVI clgorithm configuration.

Fields:

  * `linar_solver`: Linear solver to use, must be suitable for positive-definite operators
  * `optimizer`: Optimization solver to use
  * `optimizer_opts`: Optimization solver options

`linsolver` must be a solver supported by [`LinearSolve`](https://github.com/SciML/LinearSolve.jl) or [`MGVI.MatrixInversion`](@ref). Use `MatrixInversion` only for low-dimensional problems.

`optimizer` nay be [`MGVI.NewtonCG()`](@ref) or an optimization algorithm supported by `Optimization` or `Optim`. `optimizer_opts` is algorithm-specific.
