```
run_reopt(ms::AbstractArray{T, 1}, p::REoptInputs) where T <: JuMP.AbstractModel
```

Solve the `Scenario` and `BAUScenario` in parallel using the first two (empty) models in `ms` and inputs from `p`.
