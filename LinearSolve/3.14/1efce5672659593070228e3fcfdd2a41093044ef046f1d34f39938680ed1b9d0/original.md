`HYPREAlgorithm(solver; Pl = nothing)`

[HYPRE.jl](https://github.com/fredrikekre/HYPRE.jl) is an interface to [`hypre`](https://computing.llnl.gov/projects/hypre-scalable-linear-solvers-multigrid-methods) and provide iterative solvers and preconditioners for sparse linear systems. It is mainly developed for large multi-process distributed problems (using MPI), but can also be used for single-process problems with Julias standard sparse matrices.

If you need more fine-grained control over the solver/preconditioner options you can alternatively pass an already created solver to `HYPREAlgorithm` (and to the `Pl` keyword argument). See HYPRE.jl docs for how to set up solvers with specific options.

!!! note
    Using HYPRE solvers requires Julia version 1.9 or higher, and that the package HYPRE.jl is installed.


## Positional Arguments

The single positional argument `solver` has the following choices:

  * `HYPRE.BiCGSTAB`
  * `HYPRE.BoomerAMG`
  * `HYPRE.FlexGMRES`
  * `HYPRE.GMRES`
  * `HYPRE.Hybrid`
  * `HYPRE.ILU`
  * `HYPRE.ParaSails` (as preconditioner only)
  * `HYPRE.PCG`

## Keyword Arguments

  * `Pl`: A choice of left preconditioner.

## Example

For example, to use `HYPRE.PCG` as the solver, with `HYPRE.BoomerAMG` as the preconditioner, the algorithm should be defined as follows:

```julia
A, b = setup_system(...)
prob = LinearProblem(A, b)
alg = HYPREAlgorithm(HYPRE.PCG)
prec = HYPRE.BoomerAMG
sol = solve(prob, alg; Pl = prec)
```
