```
solution_statuses!(pm::AbstractUnbalancedPowerModel, sol::Dict{String,Any})
```

Converts all `status` fields in a solution `sol` from Float64 to `Status` enum, for all time steps.
