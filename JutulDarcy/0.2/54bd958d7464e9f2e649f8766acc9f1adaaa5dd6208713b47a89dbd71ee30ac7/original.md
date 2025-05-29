```
setup_reservoir_simulator(case::JutulCase; <keyword arguments>)
```

# Keyword arguments

  * `mode=:default`: Mode used for solving. Can be set to `:mpi` if running in MPI mode together with HYPRE, PartitionedArrays and MPI in your environment.
  * `method=:newton`: Can be `:newton`, `:nldd` or `:aspen`. Newton is the most tested approach and `:nldd` can speed up difficult models. The `:nldd` option enables a host of additional options (look at the simulator config for more details).
  * `presolve_wells=false`: Solve wells before each linearization. Can improve convergence for models with multisegment wells.

## Linear solver options

  * `linear_solver=:bicgstab`: iterative solver to use (provided model supports it). Typical options are `:bicgstab` or `:gmres` Can alternatively pass a linear solver instance.
  * `precond=:cpr`: preconditioner for iterative solver. For larger problems, CPR variants are recommended. In order of strength and cost:

      * `:cpr` standard Constrained-Pressure-Residual with ILU(0) second stage (strong preconditioner)
      * `:cprw` CPRW with ILU(0) second stage. Faster for problems with wells (strong preconditioner)
      * `:ilu0` block-incomplete-LU (intermediate strength preconditioner)
      * `:spai0`: Sparse Approximate Inverse of lowest order (weak preconditioner)
      * `jacobi`: Jacobi preconditioner (weak preconditioner)
  * `rtol=nothing`: relative tolerance for linear solver. If set to `nothing`, the default tolerance for the preconditioner is used, which is 5e-3 for CPR variants and 1e-2 for smoothers.
  * `linear_solver_arg`: `Dict` containing additional linear solver arguments.

## Timestepping options

  * `initial_dt=si_unit(:day)`: initial timestep in seconds (one day by default)
  * `target_ds=Inf`: target saturation change over a timestep used by timestepper.
  * `target_dz=Inf`: target mole fraction change over a timestep used by timestepper (compositional only).
  * `target_its=8`: target number of nonlinear iterations per time step
  * `offset_its=1`: dampening parameter for time step selector where larger values lead to more pessimistic estimates.
  * `timesteps=:auto`: Set to `:auto` to use automatic timestepping, `:none` for no automatic timestepping (i.e. try to solve exact report steps)
  * `max_timestep=si_unit(:year)`: Maximum internal timestep used in solver.
  * `min_timestep=0.0`: Minimum internal timestep used in solver.

## Convergence criterions

  * `tol_cnv=1e-3`: maximum allowable point-wise error (volume-balance)
  * `tol_mb=1e-7`: maximum alllowable integrated error (mass-balance)
  * `tol_cnv_well=10*tol_cnv`: maximum allowable point-wise error for well node (volume-balance)
  * `tol_mb_well=1e4*tol_mb`: maximum alllowable integrated error for well node (mass-balance)
  * `inc_tol_dp_abs=Inf`: Maximum allowable pressure change (absolute)
  * `inc_tol_dp_rel=Inf`: Maximum allowable pressure change (absolute)
  * `inc_tol_dz=Inf`: Maximum allowable composition change (compositional only).

## Inherited keyword arguments

Additional keyword arguments come from the base Jutul simulation framework. We list a few of the most relevant entries here for convenience:

  * `info_level = 0`: Output level. Set to 0 for minimal output, -1 for no output and 1 or more for increasing verbosity.
  * `output_path`: Path to write output to.
  * `max_nonlinear_iterations=15`: Maximum Newton iterations before a time-step is cut.
  * `min_nonlinear_iterations=1`: Minimum number of Newtons to perform before checking convergence.
  * `relaxation=Jutul.NoRelaxation()`: Dampening used for solves. Can be set to `Jutul.SimpleRelaxation()` for difficult models. Equivialent option is to set `true` for relaxation and `false` for no relaxation.
  * `failure_cuts_timestep=true`: Cut timestep instead of throwing an error when numerical issues are encountered (e.g. linear solver divergence).
  * `max_timestep_cuts=25`: Maximum number of timestep cuts before a solver gives up. Note that when using dynamic timestepping, this in practice defines a minimal timestep, with more than the prescribed number of cuts being allowed if the timestep is dynamically increased after cutting.
  * `timestep_max_increase=10.0`: Max allowable factor to increase time-step by. Overrides any choices made in dynamic step selection.
  * `timestep_max_decrease=0.1`: Max allowable factor to decrease time-step by. Overrides any choices made in dynamic step selection.
  * `tol_factor_final_iteration=1.0`: If set to a value larger than 1.0, the final convergence check before a time-step is cut is relaxed by multiplying all tolerances with this value. Warning: Setting it to a large value can have severe impact on numerical accuracy. A value of 1 to 10 is typically safe if your default tolerances are strict.
