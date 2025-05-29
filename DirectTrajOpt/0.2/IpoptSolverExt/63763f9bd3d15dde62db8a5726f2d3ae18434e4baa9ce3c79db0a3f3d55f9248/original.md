solve!(prob::DirectTrajOptProblem;         init*traj=nothing,         save*path=nothing,         max*iter=prob.ipopt*options.max*iter,         linear*solver=prob.ipopt*options.linear*solver,         print*level=prob.ipopt*options.print*level,         remove*slack*variables=false,         callback=nothing         # state*type=:unitary,         # print_fidelity=false,     )

```
Call optimization solver to solve the quantum control problem with parameters and callbacks.
```

# Arguments

  * `prob::DirectTrajOptProblem`: The quantum control problem to solve.
  * `init_traj::NamedTrajectory`: Initial guess for the control trajectory. If not provided, a random guess will be generated.
  * `save_path::String`: Path to save the problem after optimization.
  * `max_iter::Int`: Maximum number of iterations for the optimization solver.
  * `linear_solver::String`: Linear solver to use for the optimization solver (e.g., "mumps", "paradiso", etc).
  * `print_level::Int`: Verbosity level for the solver.
  * `callback::Function`: Callback function to call during optimization steps.
