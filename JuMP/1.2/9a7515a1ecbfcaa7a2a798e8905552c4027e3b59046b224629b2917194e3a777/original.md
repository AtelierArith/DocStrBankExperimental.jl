```
delete(model::Model, variable_refs::Vector{VariableRef})
```

Delete the variables associated with `variable_refs` from the model `model`. Solvers may implement methods for deleting multiple variables that are more efficient than repeatedly calling the single variable delete method.

See also: [`unregister`](@ref)
