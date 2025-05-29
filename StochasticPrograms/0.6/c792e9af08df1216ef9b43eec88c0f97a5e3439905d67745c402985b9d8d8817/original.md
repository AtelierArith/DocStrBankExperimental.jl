```
fix(dvar::DecisionVariable, val::Number)
```

Fix the first-stage decision associated with `dvar` to `val`. In contexts where `dvar` is a variable, the variable is fixed to the value. In contexts where `dvar` is a known parameter value, the value is updated.
