```
advance_until_time!(DiffEQ::Module, TCS::TimeControlSolver, timestep, finaltime; solver = nothing, abstol = 1e-1, reltol = 1e-1, dtmin = 0, adaptive::Bool = true)
```

Advances a TimeControlSolver in time with the given (initial) timestep until the specified finaltime is reached (up to the specified tolerance) with the given exterior time integration module. The only valid Module here is DifferentialEquations.jl and the optional arguments are passed to it. If solver == nothing the solver Rosenbrock23(autodiff = false) will be chosen. For more choices please consult the documentation of DifferentialEquations.jl.

Also note that this is a highly experimental feature and will not work for general TimeControlSolvers configuration (e.g. in the case of several subiterations or, it seems, saddle point problems). Also have a look at corressponding the example in the advanced examples section.
