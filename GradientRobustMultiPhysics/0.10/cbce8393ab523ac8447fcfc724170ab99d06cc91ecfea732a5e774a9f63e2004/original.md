```
SolverConfig{T,TvG,TiG}(PDE::PDEDescription; kwargs...) where {T,TvG,TiG}
```

Generates a solver configuration (that can used for triggering assembly manually).

Keyword arguments:

  * anderson_iterations: use Anderson acceleration with this many previous iterates (to hopefully speed up/enable convergence of fixpoint iterations). Default: 0
  * subiterations: an array of equation subsets (each an array) that should be solved together in each fixpoint iteration. Default: ''auto''
  * show*iteration*details: show details (residuals etc.) of each iteration. Default: true
  * anderson_unknowns: an array of unknown numbers that should be included in the Anderson acceleration. Default: [1]
  * show_statistics: show some statistics like assembly times. Default: false
  * anderson_metric: String that encodes the desired convergence metric for the Anderson acceleration (possible values: ''l2'' or ''L2'' or ''H1''). Default: ''l2''
  * skip*update: matrix update (for the j-th sub-iteration) will be performed each skip*update[j] iteration; -1 means only in the first iteration. Default: [1]
  * linsolver: String that encodes the linear solver, or type name of self-defined solver (see corressponding example), or type name of ExtendableSparse.AbstractFactorization. Default: ''UMFPACK''
  * damping: damp the new iteration with this part of the old iteration (0 = undamped), also a function is allowed with the interface (old*iterate, new*iterate, fixed_dofs) that returns the new damping value. Default: 0
  * time: time at which time-dependent data functions are evaluated or initial time for TimeControlSolver. Default: 0
  * parallel_storage: assemble storaged operators in parallel for loop. Default: false
  * show*solver*config: show the complete solver configuration before starting to solve. Default: false
  * anderson_damping: Damping factor in Anderson acceleration (1 = undamped). Default: 1
  * check*nonlinear*residual: check the nonlinear residual in last nonlinear iteration (causes one more reassembly of nonlinear terms). Default: ''auto''
  * fixed_penalty: penalty that is used for the values of fixed degrees of freedom (e.g. by Dirichlet boundary data or global constraints). Default: 1.0e60
  * target_residual: stop fixpoint iterations if the (nonlinear) residual is smaller than this number. Default: 1.0e-10
  * maxiterations: maximal number of nonlinear iterations (TimeControlSolver runs that many in each time step). Default: ''auto''
