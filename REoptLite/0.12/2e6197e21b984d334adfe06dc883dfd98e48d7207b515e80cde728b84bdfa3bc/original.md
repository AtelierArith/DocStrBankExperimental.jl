```
run_reopt(ms::AbstractArray{T, 1}, fp::String) where T <: JuMP.AbstractModel
```

Solve the `Scenario` and `BAUScenario` in parallel using the first two (empty) models in `ms` and inputs defined in the JSON file at the filepath `fp`.
