```
JuMP.value(vref::GeneralVariableRef; [result::Int = 1, 
           label::Type{<:AbstractSupportLabel} = PublicLabel,
           ndarray::Bool = false, kwargs...])
```

Extend `JuMP.value` to return the value(s) of `vref` in accordance with its  reformulation variable(s) stored in the optimizer model and the result index  `result` of the most recent solution obtained. Use [`JuMP.has_values`](@ref JuMP.has_values(::InfiniteModel)) to check if a result exists before asking for values. 

The keyword arugments `label` and `ndarray` are what `TranscriptionOpt` employ  and `kwargs` denote extra ones that user extensions may employ.

By default only the values associated with public supports are returned, the  full set can be accessed via `label = All`. Moreover, the values of infinite  variables are returned as a list. However, a n-dimensional array  can be obtained via `ndarray = true` which is handy when the variable has multiple  infinite parameter dependencies.

To provide context for the results it may be helpful to also query the variable's `parameter_refs` and `supports` which will have a one-to-one correspondence with the value(s). It may also be helpful to query via [`optimizer_model_variable`](@ref) to retrieve the variables(s) that these values are based on. These functions should  all be called with the same keyword arugments for consistency.

For extensions, this only works if [`optimizer_model_variable`](@ref) has been extended correctly and/or [`map_value`](@ref) has been extended for variables.

**Example**

```julia-repl
julia> value(z)
42.0
```
