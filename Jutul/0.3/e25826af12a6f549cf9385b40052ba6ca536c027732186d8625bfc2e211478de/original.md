```
setup_parameters(model::JutulModel; name = value)
```

Set up a parameter storage for a given model with values for the parameter defined in the model.

# Arguments

  * `name=value`: The name of the parameter together with the value(s) of the parameter.

A scalar (or short vector of the right size for [`VectorVariables`](@ref)) will be repeated over the entire domain, while a vector (or matrix for [`VectorVariables`](@ref)) with length (number of columns for [`VectorVariables`](@ref)) equal to the entity count (for example, number of cells for a cell variable) will be used directly.
