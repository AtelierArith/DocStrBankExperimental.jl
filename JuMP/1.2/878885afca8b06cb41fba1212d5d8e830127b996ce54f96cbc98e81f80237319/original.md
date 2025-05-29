```
delete(model::Model, con_ref::ConstraintRef)
```

Delete the constraint associated with `constraint_ref` from the model `model`.

Note that `delete` does not unregister the name from the model, so adding a new constraint of the same name will throw an error. Use [`unregister`](@ref) to unregister the name after deletion as follows:

```julia
@constraint(model, c, 2x <= 1)
delete(model, c)
unregister(model, :c)
```

See also: [`unregister`](@ref)
