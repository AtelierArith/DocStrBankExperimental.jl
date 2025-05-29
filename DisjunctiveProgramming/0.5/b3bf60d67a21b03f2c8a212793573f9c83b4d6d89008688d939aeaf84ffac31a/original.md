```
JuMP.fix(vref::LogicalVariableRef, value::Bool)::Nothing
```

Fix a logical variable to a value. Update the fixing constraint if one exists, otherwise create a new one.
