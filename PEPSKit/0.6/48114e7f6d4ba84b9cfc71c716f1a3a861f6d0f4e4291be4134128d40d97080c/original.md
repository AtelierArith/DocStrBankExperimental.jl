```julia
struct LinSolver{F} <: PEPSKit.GradMode{F}
```

Gradient mode wrapper around `KrylovKit.LinearSolver` for solving the gradient linear problem using iterative solvers.

## Fields

  * `solver_alg::KrylovKit.LinearSolver`

## Constructors

```
LinSolver(; kwargs...)
```

Construct the `LinSolver` algorithm struct based on the following keyword arguments:

  * `tol::Real=1.0e-6` : Convergence tolerance of the linear solver.
  * `maxiter::Int=30` : Maximal number of solver iterations.
  * `verbosity::Int=-1` : Output information verbosity of the linear solver.
  * `iterscheme::Symbol=:fixed` : Style of CTMRG iteration which is being differentiated, which can be:

      * `:fixed` : the differentiated CTMRG iteration uses a pre-computed SVD with a fixed set of gauges
      * `:diffgauge` : the differentiated iteration consists of a CTMRG iteration and a subsequent gauge-fixing step such that the gauge-fixing procedure is differentiated as well
  * `solver_alg::Union{KrylovKit.LinearSolver,NamedTuple}=(; alg::Symbol=:bicgstab` : Linear solver algorithm which, if supplied directly as a `KrylovKit.LinearSolver` overrides the above specified `tol`, `maxiter` and `verbosity`. Alternatively, it can be supplied via a `NamedTuple` where `alg` can be one of the following:

      * `:gmres` : GMRES iterative linear solver, see [`KrylovKit.GMRES`](@extref) for details
      * `:bicgstab` : BiCGStab iterative linear solver, see [`KrylovKit.BiCGStab`](@extref) for details
