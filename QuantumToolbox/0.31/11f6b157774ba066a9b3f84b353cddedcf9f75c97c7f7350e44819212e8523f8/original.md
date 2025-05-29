```
SSFloquetEffectiveLiouvillian(steadystate_solver = SteadyStateDirectSolver())
```

A solver which solves [`steadystate_fourier`](@ref) by first extracting an effective time-independent Liouvillian and then using the `steadystate_solver` to extract the steadystate..

# Parameters

  * `steadystate_solver::SteadyStateSolver=SteadyStateDirectSolver()`: The solver to use for the effective Liouvillian.

!!! note
    This solver is only available for [`steadystate_fourier`](@ref).

