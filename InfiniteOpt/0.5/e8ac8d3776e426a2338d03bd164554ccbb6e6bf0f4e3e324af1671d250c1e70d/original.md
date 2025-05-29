```
optimizer_model_variable(vref::GeneralVariableRef; 
                         [label::Type{<:AbstractSupportLabel} = PublicLabel, 
                         ndarray::Bool = false,
                         kwargs...])
```

Return the reformulation variable(s) stored in the optimizer model that correspond to `vref`. Also errors if no such variable can be found in the optimizer model.

The keyword arugments `label` and `ndarray` are what `TranscriptionOpt` employ  and `kwargs` denote extra ones that user extensions may employ in accordance with their implementation of [`optimizer_model_variable`](@ref). Errors if such an extension has not been written. 

By default only the variables associated with public supports are returned, the  full set can be accessed via `label = All`. Moreover, infinite variables are  returned as a list corresponding to their supports. However, a n-dimensional array  can be obtained via `ndarray = true` which is handy when the variable has multiple  infinite parameter dependencies. The corresponding supports are obtained via  `supports` using the same keyword arguments.

**Example**

```julia-repl
julia> optimizer_model_variable(x) # infinite variable
2-element Array{VariableRef,1}:
 x(support: 1)
 x(support: 2)

julia> optimizer_model_variable(z) # finite variable
z
```
