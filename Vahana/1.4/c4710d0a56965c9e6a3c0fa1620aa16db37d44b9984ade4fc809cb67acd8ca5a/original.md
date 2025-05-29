```
create_model(types::ModelTypes, name::String)
```

Creates a struct that is a subtype of the `Simulation` type and methods corresponding to the type information of `types` to the Julia session. The new structure is named `name`, and all methods are specific to this structure using Julia's multiple dispatch concept, so it is possible to have different models in the same Julia session (as long as `name` is different).

Returns a [`Model`](@ref) that can be used in [`create_simulation`](@ref) to create a concrete simulation.  
