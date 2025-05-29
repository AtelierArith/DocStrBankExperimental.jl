```
make_disaggregated_variable(
    model::JuMP.AbstractModel, 
    vref::JuMP.AbstractVariableRef, 
    name::String, 
    lower_bound::Number, 
    upper_bound::Number
    )::JuMP.AbstractVariableRef
```

Creates and adds a variable to `model` with name `name` and bounds `lower_bound`  and `upper_bound` based on the original variable `vref`. This is used to  create dissagregated variables needed for the [`Hull`](@ref) reformulation. This is implemented for `model::JuMP.GenericModel` and  `vref::JuMP.GenericVariableRef`, but it serves as an extension point for  interfaces with other model/variable reference types. This also requires  the implementation of [`requires_disaggregation`](@ref).
