```
EulerAcousticsCouplingCallback(ode_euler, averaging_file::AbstractString, alg,
                               cfl_acoustics::Real, cfl_euler::Real; kwargs...)
```

!!! warning "Experimental code"
    This callback is experimental and may change in any future release.


Creates an [`EulerAcousticsCouplingCallback`](@ref) based on the pure flow `ODEProblem` given by `ode_euler`. Creates an integrator using the time integration method `alg` and the keyword arguments to solve `ode_euler` (consult the [OrdinaryDiffEq documentation](https://diffeq.sciml.ai/stable/) for further information). Manages the step size for both solvers by using the minimum of the maximum step size obtained with CFL numbers `cfl_acoustics` for the acoustics solver and `cfl_euler` for and flow solver, respectively. The mean values for the acoustic perturbation equations are read from `averaging_file` (see [`AveragingCallback`](@ref)).
