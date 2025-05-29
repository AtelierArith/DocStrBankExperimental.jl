```
SolverControl
SolverControl(;kwargs...)
```

Solver control parameter for time stepping, embedding, Newton method and linear solver control. All field names can be used as keyword arguments for [`solve(system::VoronoiFVM.AbstractSystem; kwargs...)`](@ref)

Newton's method solves $F(u)=0$ by the iterative procedure $u_{i+1}=u_{i} - d_i F'(u_i)^{-1}F(u_i)$ starting with some initial value $u_0$, where $d_i$ is a damping parameter.

  * `verbose::Union{Bool, String}`: Verbosity control. A collection of output categories is given in a string composed of the following letters:

      * a: allocation warnings
      * d: deprecation warnings
      * e: time/parameter evolution log
      * n: newton solver log
      * l: linear solver log

    Alternatively, a Bool value can be given, resulting in

      * true: "neda"
      * false: "da"

    Switch off all output including deprecation warnings via `verbose=""`. In the output, corresponding messages are marked e.g. via '[n]', `[a]` etc. (besides of '[l]')

    For switching between printing output and logging output, see [`log_output!`](@ref) and [`print_output!`](@ref) .

  * `abstol::Float64`: Tolerance (in terms of norm of Newton update): terminate if $\Delta u_i=||u_{i+1}-u_i||_\infty <$ `abstol`.

  * `reltol::Float64`: Tolerance (relative to the size of the first update): terminate if $\Delta u_i/\Delta u_1<$ `reltol`.

  * `maxiters::Int64`: Maximum number of newton iterations.

  * `tol_round::Float64`: Tolerance for roundoff error detection: terminate if   $|\;||u_{i+1}||_1 - ||u_{i}||_1\;|/ ||u_{i}||_1<$ `tol_round` occurred `max_round` times in a row.

  * `tol_mono::Float64`: Tolerance for monotonicity test: terminate with error if $\Delta u_i/\Delta u_{i-1}>$ `1/tol_mono`.

  * `damp_initial::Float64`: Initial damping parameter $d_0$. To handle convergence problems, set this to a value less than 1.

  * `damp_growth::Float64`: Damping parameter growth factor: $d_{i+1}=\min(d_i\cdot$ `max_growth` $,1)$. It should be larger than 1.

  * `max_round::Int64`: Maximum number of consecutive iterations within roundoff error tolerance The default effectively disables this criterion.

  * `unorm::Function`: Calculation of Newton update norm

  * `rnorm::Function`: Functional for roundoff error calculation

  * `method_linear::Union{Nothing, LinearSolve.SciMLLinearSolveAlgorithm}`: Solver method for linear systems (see LinearSolve.jl). If given `nothing`, as default are chosen:

      * `UMFPACKFactorization()` for sparse matrices with Float64
      * `SparspakFactorization()` for sparse matrices with  general number types.
      * Defaults from LinearSolve.jl for tridiagonal and banded matrices

    Users should experiment with what works best for their problem.

    For an overeview on possible alternatives, see [`VoronoiFVM.LinearSolverStrategy`](@ref).

  * `reltol_linear::Float64`:     Relative tolerance of iterative linear solver.

  * `abstol_linear::Float64`: Absolute tolerance of iterative linear solver.

  * `maxiters_linear::Int64`: Maximum number of iterations of linear solver

  * `precon_linear::Union{Nothing, Function, ExtendableSparse.AbstractFactorization, LinearSolve.SciMLLinearSolveAlgorithm, Type}`: Constructor for preconditioner for linear systems. This should work as a function `precon_linear(A)` which takes an AbstractSparseMatrixCSC (e.g. an ExtendableSparseMatrix) and returns a preconditioner object in the sense of `LinearSolve.jl`, i.e. which has an `ldiv!(u,A,v)` method. Useful examples:

      * `ExtendableSparse.ILUZero`
      * `ExtendableSparse.Jacobi`

    For easy access to this functionality, see see also [`VoronoiFVM.LinearSolverStrategy`](@ref).

  * `keepcurrent_linear::Bool`: Update preconditioner in each Newton step ? Translates to `reuse_precs=!keepcurrent_linear` for LinearSolve.

  * `Δp::Float64`: Initial parameter step for embedding.

  * `Δp_max::Float64`: Maximal parameter step size.

  * `Δp_min::Float64`: Minimal parameter step size.

  * `Δp_grow::Float64`: Maximal parameter step size growth.

  * `Δp_decrease::Float64`: Parameter step decrease factor upon rejection

  * `Δt::Float64`: Initial time step  size.

  * `Δt_max::Float64`: Maximal time step size.

  * `Δt_min::Float64`: Minimal time step size.

  * `Δt_grow::Float64`: Maximal time step size growth.

  * `Δt_decrease::Float64`: Time step decrease factor upon rejection

  * `Δu_opt::Float64`: Optimal size of update for time stepping and embedding. The algorithm tries to keep the difference in norm between "old" and "new" solutions  approximately at this value.

  * `Δu_max_factor::Float64`: Control maximum  sice of update `Δu` for time stepping and embedding relative to `Δu_opt`. Time steps with `Δu > Δu_max_factor*Δu_opt` will be rejected.

  * `force_first_step::Bool`: Force first timestep.

  * `num_final_steps::Int64`: Number of final steps to adjust at end of time interval in order to prevent breakdown of step size.

  * `handle_exceptions::Bool`: Handle exceptions during transient solver and parameter embedding. If `true`, exceptions in Newton solves are caught, the embedding resp. time step is lowered, and solution is retried. Moreover, if embedding or time stepping fails (e.g. due to reaching minimal step size), a warning is issued, and a solution is returned with all steps calculated so far.

    Otherwise (by default) errors are thrown.

  * `store_all::Bool`: Store all steps of transient/embedding problem:

  * `in_memory::Bool`: Store transient/embedding solution in memory

  * `log::Any`:    Record history

  * `edge_cutoff::Float64`: Edge parameter cutoff for rectangular triangles.

  * `pre::Function`: Function `pre(sol,t)` called before time/embedding step

  * `post::Function`: Function `post(sol,oldsol,t,Δt)` called after successful time/embedding step

  * `sample::Function`: Function `sample(sol,t)` to be called for each `t in times[2:end]`

  * `delta::Function`: Time step error estimator. A function `Δu=delta(system,u,uold,t,Δt)` to calculate `Δu`.

  * `tol_absolute::Union{Nothing, Float64}`
  * `tol_relative::Union{Nothing, Float64}`
  * `damp::Union{Nothing, Float64}`
  * `damp_grow::Union{Nothing, Float64}`
  * `max_iterations::Union{Nothing, Int64}`
  * `tol_linear::Union{Nothing, Float64}`
  * `max_lureuse::Union{Nothing, Int64}`
  * `mynorm::Union{Nothing, Function}`
  * `myrnorm::Union{Nothing, Function}`
