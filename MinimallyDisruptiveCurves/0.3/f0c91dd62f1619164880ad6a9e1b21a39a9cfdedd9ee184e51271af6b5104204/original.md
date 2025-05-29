```
evolve(c::CurveProblem, solmethod=Tsit5; mdc_callback=nothing, callback=nothing, saved_values=nothing, momentum_tol=1e-3,kwargs...)
```

Evolves a minimally disruptive curve, with curve parameters specified by curveProblem. Uses DifferentialEquations.solve() to run the ODE. MinimallyDisruptiveCurves.jl callbacks go in the `mdc_callback` keyword argument. You can also use any DifferentialEquations.jl callbacks compatible with DifferentialEquations.solve(). They go in the `callback` keyword argument
