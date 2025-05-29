```
JuMP.optimizer_index(vref::GeneralVariableRef; 
                     [label::Type{<:AbstractSupportLabel} = PublicLabel,
                     ndarray::Bool = false, kwargs...])
```

Extend `JuMP.optimizer_index` to return the `MathOptInterface` index(es) of  `vref` in accordance with its reformulation variable(s) stored in the optimizer  model.

The keyword arugments `label` and `ndarray` are what `TranscriptionOpt` employ  and `kwargs` denote extra ones that user extensions may employ.

By default only the optimizer indices associated with public supports are returned, the  full set can be accessed via `label = All`. Moreover, the indices of infinite  variables are returned as a list. However, a n-dimensional array  can be obtained via `ndarray = true` which is handy when the variable has multiple  infinite parameter dependencies.

It may also be helpful to query via [`optimizer_model_variable`](@ref) to retrieve the variables(s) that these indices are based on. These should use the  same keyword arguments for consistency.

For extensions, this only works if [`optimizer_model_variable`](@ref) has been extended correctly and/or [`map_optimizer_index`](@ref) has been extended for variables.

**Example**

```julia-repl
julia> optimizer_index(x)
4-element Array{MathOptInterface.VariableIndex,1}:
 MathOptInterface.VariableIndex(2)
 MathOptInterface.VariableIndex(3)
 MathOptInterface.VariableIndex(4)
 MathOptInterface.VariableIndex(5)
```
