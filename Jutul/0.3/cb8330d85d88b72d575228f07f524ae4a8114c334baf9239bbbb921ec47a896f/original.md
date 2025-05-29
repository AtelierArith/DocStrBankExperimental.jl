```
setup_state(model::JutulModel, name1 = value1, name2 = value2)
```

Set up a state for a given model with values for the primary variables defined in the model. Normally all primary variables must be initialized in this way.

# Arguments

  * `name=value`: The name of the primary variable together with the value(s) used to initialize the primary variable.

A scalar (or short vector of the right size for [`VectorVariables`](@ref)) will be repeated over the entire domain, while a vector (or matrix for [`VectorVariables`](@ref)) with length (number of columns for [`VectorVariables`](@ref)) equal to the entity count (for example, number of cells for a cell variable) will be used directly.

Note: You likely want to overload [`setup_state!`]@ref for a custom model instead of `setup_state`
