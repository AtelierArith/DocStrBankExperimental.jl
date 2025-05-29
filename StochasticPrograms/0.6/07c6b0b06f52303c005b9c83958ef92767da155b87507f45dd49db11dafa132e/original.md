```
unfix(dvar::DecisionVariable, scenario_index::Integer)
```

Unfix the scenario-dependent decision associated with `dvar` at `scenario_index`. If the decision is already in a `NotTaken` state, this does nothing.
