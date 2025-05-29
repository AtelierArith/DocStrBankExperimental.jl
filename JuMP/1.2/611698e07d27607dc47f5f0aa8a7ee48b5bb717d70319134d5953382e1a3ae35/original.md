```
delete(model::Model, variable_ref::VariableRef)
```

Delete the variable associated with `variable_ref` from the model `model`.

Note that `delete` does not unregister the name from the model, so adding a new variable of the same name will throw an error. Use [`unregister`](@ref) to unregister the name after deletion as follows:

```julia
@variable(model, x)
delete(model, x)
unregister(model, :x)
```

See also: [`unregister`](@ref)
