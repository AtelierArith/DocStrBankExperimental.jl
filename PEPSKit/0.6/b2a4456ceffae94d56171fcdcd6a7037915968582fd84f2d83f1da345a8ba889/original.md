```julia
struct EigSolver{F} <: PEPSKit.GradMode{F}
```

Gradient mode wrapper around `KrylovKit.KrylovAlgorithm` for solving the gradient linear problem as an eigenvalue problem.

## Fields

  * `solver_alg::KrylovKit.KrylovAlgorithm`

## Constructors

```
EigSolver(; kwargs...)
```

Construct the `EigSolver` algorithm struct based on the following keyword arguments:

  * `tol::Real=1.0e-6` : Convergence tolerance of the eigen solver.
  * `maxiter::Int=30` : Maximal number of solver iterations.
  * `verbosity::Int=-1` : Output information verbosity of the linear solver.
  * `iterscheme::Symbol=:fixed` : Style of CTMRG iteration which is being differentiated, which can be:

      * `:fixed` : the differentiated CTMRG iteration uses a pre-computed SVD with a fixed set of gauges
      * `:diffgauge` : the differentiated iteration consists of a CTMRG iteration and a subsequent gauge-fixing step such that the gauge-fixing procedure is differentiated as well
  * `solver_alg::Union{KrylovKit.KrylovAlgorithm,NamedTuple}=(; alg=:arnoldi` : Eigen solver algorithm which, if supplied directly as a `KrylovKit.KrylovAlgorithm` overrides the above specified `tol`, `maxiter` and `verbosity`. Alternatively, it can be supplied via a `NamedTuple` where `alg` can be one of the following:

      * `:arnoldi` : Arnoldi Krylov algorithm, see [`KrylovKit.Arnoldi`](@extref) for details
