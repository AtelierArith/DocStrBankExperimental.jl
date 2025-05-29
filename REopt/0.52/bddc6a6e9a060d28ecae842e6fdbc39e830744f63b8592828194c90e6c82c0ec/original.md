```
run_mpc(m::JuMP.AbstractModel,  d::Dict)
```

Solve the model predictive control problem using the `MPCScenario` defined in the dict `d`.

Returns a Dict of results with keys matching those in the `MPCScenario`.
