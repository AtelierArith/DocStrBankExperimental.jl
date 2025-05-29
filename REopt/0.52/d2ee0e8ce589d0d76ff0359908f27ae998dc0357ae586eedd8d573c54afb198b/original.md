```
run_mpc(m::JuMP.AbstractModel, p::MPCInputs)
```

Solve the model predictive control problem using the `MPCInputs`.

Returns a Dict of results with keys matching those in the `MPCScenario`.
