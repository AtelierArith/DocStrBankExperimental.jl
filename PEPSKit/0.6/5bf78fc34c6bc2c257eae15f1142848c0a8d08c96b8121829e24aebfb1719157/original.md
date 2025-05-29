```
fixedpoint(operator, peps₀::InfinitePEPS, env₀::CTMRGEnv; kwargs...) -> peps_final, env_final, cost_final, info
# expert version:
fixedpoint(operator, peps₀::InfinitePEPS, env₀::CTMRGEnv, alg::PEPSOptimize; finalize!=OptimKit._finalize!)
```

Find the fixed point of `operator` (i.e. the ground state) starting from `peps₀` according to the supplied optimization parameters. The initial environment `env₀` serves as an initial guess for the first CTMRG run. By default, a random initial environment is used.

The optimization parameters can be supplied via the keyword arguments or directly as a `PEPSOptimize` struct. The following keyword arguments are supported:

## Keyword arguments

### General settings

  * `tol::Real=0.0001` : Overall tolerance for gradient norm convergence of the optimizer. Sets related tolerance such as the boundary and boundary-gradient tolerances to sensible defaults unless they are explictly specified.
  * `verbosity::Int=1` : Overall output information verbosity level, should be one of the following:

    0. Suppress all output
    1. Only print warnings
    2. Initialization and convergence info
    3. Iteration info
    4. Debug info including AD outputs
  * `reuse_env::Bool=true` : If `true`, the current optimization step is initialized on the previous environment, otherwise a random environment is used.
  * `symmetrization::Union{Nothing,SymmetrizationStyle}=nothing` : Accepts `nothing` or a `SymmetrizationStyle`, in which case the PEPS and PEPS gradient are symmetrized after each optimization iteration.
  * `(finalize!)=OptimKit._finalize!` : Inserts a `finalize!` function call after each optimization step by utilizing the `finalize!` kwarg of `OptimKit.optimize`. The function maps `(peps, env), f, g = finalize!((peps, env), f, g, numiter)`.

### Boundary algorithm

Supply boundary algorithm parameters via `boundary_alg::Union{NamedTuple,<:CTMRGAlgorithm}` using either a `NamedTuple` of keyword arguments or a `CTMRGAlgorithm` directly. See [`leading_boundary`](@ref) for a description of all possible keyword arguments. By default, a CTMRG tolerance of `tol=1e-4tol` and is used.

### Gradient algorithm

Supply gradient algorithm parameters via `gradient_alg::Union{NamedTuple,Nothing,<:GradMode}` using either a `NamedTuple` of keyword arguments, `nothing`, or a `GradMode` struct directly. Pass `nothing` to fully differentiate the CTMRG run, meaning that all iterations will be taken into account, instead of differentiating the fixed point. The supported `NamedTuple` keyword arguments are:

  * `tol::Real=1e-2tol` : Convergence tolerance for the fixed-point gradient iteration.
  * `maxiter::Int=30` : Maximal number of gradient problem iterations.
  * `alg::Symbol=:linsolver` : Gradient algorithm variant, can be one of the following:

      * `:geomsum` : Compute gradient directly from the geometric sum, see [`GeomSum`](@ref)
      * `:manualiter` : Iterate gradient geometric sum manually, see [`ManualIter`](@ref)
      * `:linsolver` : Solve fixed-point gradient linear problem using iterative solver, see [`LinSolver`](@ref)
      * `:eigsolver` : Determine gradient via eigenvalue formulation of its Sylvester equation, see [`EigSolver`](@ref)
  * `verbosity::Int` : Gradient output verbosity, ≤0 by default to disable too verbose printing. Should only be >0 for debug purposes.
  * `iterscheme::Symbol=:fixed` : CTMRG iteration scheme determining mode of differentiation. This can be:

      * `:fixed` : the differentiated CTMRG iteration uses a pre-computed SVD with a fixed set of gauges
      * `:diffgauge` : the differentiated iteration consists of a CTMRG iteration and a subsequent gauge-fixing step such that the gauge-fixing procedure is differentiated as well

### Optimizer settings

Supply the optimizer algorithm via `optimizer_alg::Union{NamedTuple,<:OptimKit.OptimizationAlgorithm}` using either a `NamedTuple` of keyword arguments or a `OptimKit.OptimizationAlgorithm` directly. By default, `OptimKit.LBFGS` is used in combination with a `HagerZhangLineSearch`. The supported keyword arguments are:

  * `alg::Symbol=:lbfgs` : Optimizer algorithm, can be one of the following:

      * `:gradientdescent` : Gradient descent algorithm, see the [OptimKit README](https://github.com/Jutho/OptimKit.jl)
      * `:conjugategradient` : Conjugate gradient algorithm, see the [OptimKit README](https://github.com/Jutho/OptimKit.jl)
      * `:lbfgs` : L-BFGS algorithm, see the [OptimKit README](https://github.com/Jutho/OptimKit.jl)
  * `tol::Real=tol` : Gradient norm tolerance of the optimizer.
  * `maxiter::Int=100` : Maximal number of optimization steps.
  * `verbosity::Int=3` : Optimizer output verbosity.
  * `lbfgs_memory::Int=20` : Size of limited memory representation of BFGS Hessian matrix.

## Return values

The function returns the final PEPS, CTMRG environment and cost value, as well as an information `NamedTuple` which contains the following entries:

  * `last_gradient` : Last gradient of the cost function.
  * `fg_evaluations` : Number of evaluations of the cost and gradient function.
  * `costs` : History of cost values.
  * `gradnorms` : History of gradient norms.
  * `truncation_errors` : History of maximal truncation errors of the boundary algorithm.
  * `condition_numbers` : History of maximal condition numbers of the CTMRG environments.
  * `gradnorms_unitcell` : History of gradient norms for each respective unit cell entry.
  * `times` : History of optimization step execution times.
