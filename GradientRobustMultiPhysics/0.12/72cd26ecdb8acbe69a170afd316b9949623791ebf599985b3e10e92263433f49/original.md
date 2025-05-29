```
function TimeControlSolver(
    PDE::PDEDescription,                                        # PDE system description
    InitialValues::FEVector{T,Tv,Ti},                           # contains initial values and stores solution of advance! methods
    TIR::Type{<:AbstractTimeIntegrationRule} = BackwardEuler;   # Time integration rule
    dt_operator = [],                                           # Operator in time derivative (default: Identity) for each subiteration (applied to test and ansatz function)
    dt_action = [],                                             # Action in time derivative (deulta: NoAction) for each subiteration
    dt_is_nonlinear = [],                                          # is the time derivative nonlinear?
    T_time = Float64,                                           # Type for timestep and total time
    kwargs...) where {T,Tv,Ti}                                  # additional solver arguments
```

Creates a time-dependent solver that can be advanced in time with advance!. The FEVector Solution stores the initial state but also the solution at the current time. The argument TIR carries the time integration rule to be use (e.g. BackwardEuler or CrankNicolson). T_time determines the NumberType of the timesteps and total time.

Keyword arguments:

  * subiterations: an array of equation subsets (each an array) that should be solved together in each fixpoint iteration. Default: ''auto''
  * show*iteration*details: show details (residuals etc.) of each iteration. Default: true
  * timedependent_equations: array of the equations that should get a time derivative (only for TimeControlSolver). Default: Any[]
  * reltol: reltol for linear solver (if iterative). Default: 1.0e-12
  * show_statistics: show some statistics like assembly times. Default: false
  * skip*update: matrix update (for the j-th sub-iteration) will be performed each skip*update[j] iteration; -1 means only in the first iteration. Default: [1]
  * linsolver: any AbstractFactorization from LinearSolve.jl (default = UMFPACKFactorization). Default: LinearSolve.UMFPACKFactorization(true, true)
  * time: time at which time-dependent data functions are evaluated or initial time for TimeControlSolver. Default: 0
  * parallel_storage: assemble storaged operators in parallel for loop. Default: false
  * show*solver*config: show the complete solver configuration before starting to solve. Default: false
  * abstol: abstol for linear solver (if iterative). Default: 1.0e-12
  * check*nonlinear*residual: check the nonlinear residual in last nonlinear iteration (causes one more reassembly of nonlinear terms). Default: ''auto''
  * fixed_penalty: penalty that is used for the values of fixed degrees of freedom (e.g. by Dirichlet boundary data or global constraints). Default: 1.0e60
  * target_residual: stop fixpoint iterations if the absolute (nonlinear) residual is smaller than this number. Default: 1.0e-12
  * maxiterations: maximal number of nonlinear iterations (TimeControlSolver runs that many in each time step). Default: ''auto''

Further (very experimental) optional arguments for TimeControlSolver are:

  * dt_operator : (array of) operators applied to testfunctions in time derivative (default: Identity)
  * dt_action : (array of) actions that are applied to the ansatz function in the time derivative (to include parameters etc.)
  * dt*is*nonlinear : (array of) booleans to decide which time derivatives should be recomputed in each timestep
