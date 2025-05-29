```
optimize_design!(CH::ControlChart, rlsim_oc::Function, settings::OptSettings=OptSettings(CH); optimizer = :LN_BOBYQA, solver = :Bootstrap, hmax::Float64 = 20.0, kw...)
```

Optimizes the design of a control chart `CH` using a specified optimization algorithm.

### Arguments

  * `CH::ControlChart`: The control chart object to optimize.
  * `rlsim_oc::Function`: A function that simulates the out-of-control state of the control chart.
  * `settings::OptSettings`: The optimization settings that control the optimization routine (default: `OptSettings(CH)`).

### Keyword Arguments

  * `optimizer::Symbol`: The optimization algorithm to use (default: `:Grid`).
  * `solver::Symbol`: The root-finding algorithm to use for control limit estimation (default: `:Bootstrap`).
  * `hmax::Float64`: The maximum value of the control limit, used only when the solver is set to `:Bisection` (default: 100.0)
  * `kw...`: Additional keyword arguments to pass to the solver algorithm.

# Returns

The optimized design parameters of the control chart.
