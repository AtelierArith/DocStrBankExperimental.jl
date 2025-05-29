```
MosekModel <: MathOptInterface.AbstractModel
```

Linear variables and constraint can be deleted. For some reason MOSEK does not support deleting PSD variables.

Note also that adding variables and constraints will permanently add some (currently between 1 and 3) Int64s that a `delete!` will not remove. This ensures that Indices (Variable and constraint) that are deleted are thereafter invalid.
