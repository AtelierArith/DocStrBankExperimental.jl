```
set_objective_coefficient(model::Model, variable::VariableRef, coefficient::Real)
```

Set the linear objective coefficient associated with `Variable` to `coefficient`.

Note: this function will throw an error if a nonlinear objective is set.
