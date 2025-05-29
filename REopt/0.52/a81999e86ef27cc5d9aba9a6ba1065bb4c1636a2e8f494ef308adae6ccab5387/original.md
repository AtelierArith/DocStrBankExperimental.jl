```
run_mpc(m::JuMP.AbstractModel, fp::String)
```

Solve the model predictive control problem using the `MPCScenario` defined in the JSON file stored at the file path `fp`.

Returns a Dict of results with keys matching those in the `MPCScenario`.
