```
successful_step(ds::DynamicalSystem) -> true/false
```

Return `true` if the last `step!` call to `ds` was successful, `false` otherwise. For continuous time systems this uses DifferentialEquations.jl error checking, for discrete time it checks if any variable is `Inf` or `NaN`.
