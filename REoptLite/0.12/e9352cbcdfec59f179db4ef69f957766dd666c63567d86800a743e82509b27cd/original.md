```
run_reopt(ms::AbstractArray{T, 1}, d::Dict) where T <: JuMP.AbstractModel
```

Solve the `Scenario` and `BAUScenario` in parallel using the first two (empty) models in `ms` and inputs from `d`.
