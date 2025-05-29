```
constraint_ref_with_index(model::AbstractModel, index::MOI.ConstraintIndex)
```

Return a `ConstraintRef` of `model` corresponding to `index`.

This function is a helper function used internally by JuMP and some JuMP extensions. It should not need to be called in user-code.
