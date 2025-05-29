```
ModelTypes
```

This struct stores all (internal) information about the agent and edge types of the model and is therefore the starting point of the model definition. 

Call the ModelType constructor without parameters, and then use the created object as the first parameter in [`register_agenttype!`](@ref) and [`register_edgetype!`](@ref), whereby the |> operator can be used to concatenate these registrations.

See also [`create_model`](@ref),
