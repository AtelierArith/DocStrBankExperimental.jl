```
all_known_decision_variables(model::JuMP.Model, stage::Integer)
```

Returns a stage-wise list of all known decisions currently in the `model` at stage `stage`. The decisions are ordered by creation time.
