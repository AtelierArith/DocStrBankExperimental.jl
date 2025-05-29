```
fix(dvar::DecisionVariable, scenario_index::Integer, val::Number)
```

Fix the scenario-dependent decision associated with `dvar` at `scenario_index` to `val`. In contexts where `dvar` is a variable, the variable is fixed to the value. In contexts where `dvar` is a known parameter value, the value is updated.
