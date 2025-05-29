```
run_mpc(m::JuMP.AbstractModel, ps::AbstractVector{MPCInputs})
```

Solve the model predictive control problem using multiple `MPCInputs`.

Returns a Dict of results with keys matching those in the `MPCScenario`.
