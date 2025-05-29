```
delete(model::Model, con_refs::Vector{<:ConstraintRef})
```

Delete the constraints associated with `con_refs` from the model `model`. Solvers may implement specialized methods for deleting multiple constraints of the same concrete type, i.e., when `isconcretetype(eltype(con_refs))`. These may be more efficient than repeatedly calling the single constraint delete method.

See also: [`unregister`](@ref)
