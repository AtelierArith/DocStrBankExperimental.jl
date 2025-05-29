```
all_decision_variables(model::JuMP.Model, stage::Integer)
```

Returns a list of all decisions currently in the `model` at stage `stage`. The decisions are ordered by creation time.
