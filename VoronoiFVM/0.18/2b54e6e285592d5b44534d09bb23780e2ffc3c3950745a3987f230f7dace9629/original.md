```julia
mutable struct SolverControl
```

Solver control parameters for time stepping, embedding, Newton method control. All field names can be used as keyword arguments for [`solve(system::VoronoiFVM.AbstractSystem; kwargs...)`](@ref)

Newton's method solves $F(u)=0$ by the iterative procedure $u_{i+1}=u_{i} - d_i F'(u_i)^{-1}F(u_i)$ starting with some inital value $u_0$, where $d_i$ is a damping parameter.

  * `tol_absolute::Float64`: Tolerance (in terms of norm of Newton update): terminate if $\Delta u_i=||u_{i+1}-u_i||_\infty <$ `tol_absolute`.  Default: 1.0e-10
  * `tol_relative::Float64`: Tolerance (relative to the size of the first update): terminate if $\Delta u_i/\Delta u_1<$ `tol_relative`.  Default: 1.0e-10
  * `tol_round::Float64`: Tolerance for roundoff error detection: terminate if   $|\;||u_{i+1}||_1 - ||u_{i}||_1\;|/ ||u_{i}||_1<$ `tol_round` occured `max_round` times in a row.  Default: 1.0e-10
  * `tol_mono::Float64`: Tolerance for monotonicity test: terminate with error if $\Delta u_i/\Delta u_{i-1}>$ `1/tol_mono`.  Default: 0.001
  * `damp_initial::Float64`: Initial damping parameter $d_0$. To handle convergence problems, set this to a value less than 1.  Default: 1.0
  * `damp_growth::Float64`: Damping parameter growth factor: $d_{i+1}=\min(d_i\cdot$ `max_growth` $,1)$. It should be larger than 1.  Default: 1.2
  * `max_iterations::Int64`: Maximum number of iterations.  Default: 100
  * `max_lureuse::Int64`: Maximum number of reuses of lu factorization. It this value is 0, linear systems are solved by a sparse direct solver, and it's LU factorization is called in every Newton step. Otherwise, a BICGstab iterative method is used for linear system solution with a LU factorization as preconditioner which is updated only every `max_lureuse` Newton step.  Default: 0
  * `max_round::Int64`: Maximum number of consecutive iterations within roundoff error tolerance The default effectively disables this criterion.  Default: 1000
  * `tol_linear::Float64`: Relative tolerance of iterative linear solver.  Default: 0.0001
  * `max_iterations_linear::Int64`: Default: 20
  * `factorization::Union{Symbol, ExtendableSparse.AbstractFactorization}`: Factorization kind for linear sytems (see ExtendableSparse.jl). Possible values:

      * :lu, :default  : LU factorization from UMFPACK (for Float64) or Sparspak.jl
      * :sparspak  : LU Factorization from Sparspak
      * :pardiso  : LU Factorization from Pardiso.jl using Pardiso from pardiso.org. Install and `use` Pardiso.jl to use this option.
      * :mklpardiso  : LU Factorization from Pardiso.jl using MKL Pardiso. Install and `use` Pardiso.jl to use this option.
      * :ilu0 : Zero-fillin ILU factorization preconditioner
      * :jacobi : Jacobi (Diagonal) preconditioner

    Default: :lu
  * `max_linear_iterations::Int64`: Maximum number of iterations of linear solver  Default: 100
  * `gmres_restart::Int64`: GMRES Krylov dimension for restart  Default: 10
  * `iteration::Symbol`:  Iterative solver if factorization is incomplete. Currently supported:

      * :bicgstab : bicgstabl method from IterativeSolvers.jl
      * :cg : cg method from IterativeSolvers.jl
      * :krylov_cg : cg method from Krylov.jl
      * :krylov_bicgstab : bicgstab method from Krylov.jl
      * :krylov_gmres : gmres method from Krylov.jl

    Default: :bicgstab
  * `verbose::Bool`: Verbosity flag.  Default: false
  * `handle_exceptions::Bool`: Handle exceptions during transient solver and parameter embedding. If `true`, exceptions in Newton solves are catched, the embedding resp. time step is lowered, and solution is retried.  Default: false
  * `Δp::Float64`: Initial parameter step for embedding.  Default: 1.0
  * `Δp_max::Float64`: Maximal parameter step size.  Default: 1.0
  * `Δp_min::Float64`: Minimal parameter step size.  Default: 0.001
  * `Δp_grow::Float64`: Maximal parameter step size growth.  Default: 1.0
  * `Δt::Float64`: Initial time step  size.  Default: 0.1
  * `Δt_max::Float64`: Maximal time step size.  Default: 1.0
  * `Δt_min::Float64`: Minimal time step size.  Default: 0.001
  * `Δt_grow::Float64`: Maximal time step size growth.  Default: 1.2
  * `Δu_opt::Float64`: Optimal size of update for time stepping and embeding. The algorithm tries to keep the difference in norm between "old" and "new" solutions  approximately at this value.  Default: 0.1
  * `force_first_step::Bool`: Force first timestep.  Default: false
  * `edge_cutoff::Float64`: Edge parameter cutoff for rectangular triangles.  Default: 0.0
  * `umfpack_pivot_tolerance::Float64`: Pivot tolerance for umfpack.  Default: default*umfpack*pivot_tolerance
  * `store_all::Bool`: Store all steps of transient/embedding problem:  Default: true
  * `in_memory::Bool`: Store transient/embedding solution in memory  Default: true
  * `log::Any`: Record history  Default: false
