```
run_model(case::Case, model::EnergyModel, optimizer; check_timeprofiles = true)
```

Take the `case` data, the `model` description, and an `optimizer` to build and optimize the model. Returns the solved JuMP model.
