```
solve_decision_model(model::JuMP.Model, objective_function::Nothing=nothing; kwargs...)
```

Solve mathematical program using default objective function `@objective(model, Min, 0)`. This permits comparison to dynamic population model output.
