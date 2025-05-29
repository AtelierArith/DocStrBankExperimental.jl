```
supports(vref::DecisionVariableRef; 
         [label::Type{<:AbstractSupportLabel} = PublicLabel, 
         ndarray::Bool = false,
         kwargs...])
```

Return the supports associated with `vref` in the optimizer model. Errors if [`InfiniteOpt.variable_supports`](@ref) has not been extended for the optimizer model type or if `vref` is not be reformulated in the optimizer model.

The keyword arugments `label` and `ndarray` are what `TranscriptionOpt` employ  and `kwargs` denote extra ones that user extensions may employ in accordance with their implementation of `variable_supports`. Errors if such an extension has not been written. 

By default only the public supports are returned, the  full set can be accessed via `label = All`. Moreover, the supports of infinite  variables are returned as a list. However, a n-dimensional array  can be obtained via `ndarray = true` which is handy when the variable has multiple  infinite parameter dependencies.

**Example**

```julia-repl
julia> supports(vref)
2-element Array{Tuple{Float64},1}:
 (0.0,)
 (1.0,)
```
