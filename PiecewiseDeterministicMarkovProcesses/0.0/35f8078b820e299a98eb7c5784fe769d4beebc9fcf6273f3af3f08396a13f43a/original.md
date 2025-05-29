```
solve(problem::PDMPProblem, algo; verbose = false, n_jumps = Inf64, save_positions = (false, true), reltol = 1e-7, abstol = 1e-9, save_rate = false, finalizer = finalize_dummy, kwargs...)
```

Simulate the PDMP `problem` using the CHV algorithm.

# Arguments

  * `problem::PDMPProblem`
  * `alg` can be `CHV(ode)` (for the [CHV algorithm](https://arxiv.org/abs/1504.06873)), `Rejection(ode)` for the Rejection algorithm and `RejectionExact()` for the rejection algorithm in case the flow in between jumps is known analytically. In this latter case, `prob.F` is used for the specification of the Flow. The ODE solver `ode` can be any solver of [DifferentialEquations.jl](https://github.com/JuliaDiffEq/DifferentialEquations.jl) like `Tsit5()` for example or anyone of the list `[:cvode, :lsoda, :adams, :BDF, :euler]`. Indeed, the package implement an iterator interface which does not work yet with `ode = LSODA()`. In order to have access to the ODE solver `LSODA()`, one should use `ode = :lsoda`.
  * `verbose` display information during simulation
  * `n_jumps` maximum number of jumps to be computed
  * `save_positions` which jump position to record, pre-jump (save*positions[1] = true) and/or post-jump (save*positions[2] = true).
  * `reltol`: relative tolerance used in the ODE solver
  * `abstol`: absolute tolerance used in the ODE solver
  * `ind_save_c`: which indices of `xc` should be saved
  * `ind_save_d`: which indices of `xd` should be saved
  * `save_rate = true`: requires the solver to save the total rate. Can be useful when estimating the rate bounds in order to use the Rejection algorithm as a second try.
  * `X_extended = zeros(Tc, 1 + 1)`: (advanced use) options used to provide the shape of the extended array in the [CHV algorithm](https://arxiv.org/abs/1504.06873). Can be useful in order to use `StaticArrays.jl` for example.
  * `finalizer = finalize_dummy`: allows the user to pass a function `finalizer(rate, xc, xd, p, t)` which is called after each jump. Can be used to overload / add saving / plotting mechanisms.
  * `kwargs` keyword arguments passed to the ODE solver (from DifferentialEquations.jl)

!!! note "Solvers for the `JumpProcesses` wrapper"
    We provide a basic wrapper that should work for `VariableJumps` (the other types of jumps have not been thoroughly tested). You can use `CHV` for this type of problems. The `Rejection` solver is not functional yet.

