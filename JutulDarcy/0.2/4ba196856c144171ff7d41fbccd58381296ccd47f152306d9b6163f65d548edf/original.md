```
reservoir_linsolve(model, precond = :cpr; <keyword arguments>)
```

Set up iterative linear solver for a reservoir model from [`setup_reservoir_model`](@ref).

# Arguments

  * `model`: Reservoir model that will linearize the equations for the linear solver
  * `precond=:cpr`: Preconditioner type to use: Either :cpr (Constrained-Pressure-Residual) or :ilu0 (block-incomplete-LU) (no effect if `solver = :direct`).
  * `v=0`: verbosity (can lead to a large amount of output)
  * `solver=:bicgstab`: the symbol of a Krylov.jl solver (typically :gmres or :bicgstab)
  * `update_interval=:once`: how often the CPR AMG hierarchy is reconstructed (:once, :iteration, :ministep, :step)
  * `update_interval_partial=:iteration`: how often the pressure system is updated in CPR
  * `max_coarse`: max size of coarse level if using AMG
  * `cpr_type=nothing`: type of CPR (`:true_impes`, `:quasi_impes` or `nothing` for automatic)
  * `partial_update=true`: perform partial update of CPR preconditioner outside of AMG update (see above)
  * `rtol=1e-3`: relative tolerance for the linear solver
  * `max_iterations=100`: limit for linear solver iterations

Additional keywords are passed onto the linear solver constructor.
