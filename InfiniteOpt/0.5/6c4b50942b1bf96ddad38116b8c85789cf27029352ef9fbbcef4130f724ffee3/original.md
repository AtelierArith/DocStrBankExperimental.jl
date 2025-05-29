```
JuMP.dual(cref::InfOptConstraintRef; [result::Int = 1, 
          label::Type{<:AbstractSupportLabel} = PublicLabel,
          ndarray::Bool = false, kwargs...])
```

Extend `JuMP.dual` to return the dual(s) of `cref` in accordance with its  reformulation constraint(s) stored in the optimizer model and the result index  `result` of the most recent solution obtained. Use  [`JuMP.has_duals`](@ref JuMP.has_duals(::InfiniteModel)) to check if a result  exists before asking for duals. 

The keyword arugments `label` and `ndarray` are what `TranscriptionOpt` employ  and `kwargs` denote extra ones that user extensions may employ.

By default only the duals associated with public supports are returned, the  full set can be accessed via `label = All`. Moreover, the duals of infinite  constraints are returned as a list. However, a n-dimensional array  can be obtained via `ndarray = true` which is handy when the constraint has multiple  infinite parameter dependencies.

It may also be helpful to query via [`optimizer_model_constraint`](@ref) to retrieve the constraint(s) that these duals are based on. Calling `parameter_refs` and `supports` may also be insightful. Be sure to use the same keyword arguments for consistency.

For extensions, this only works if [`optimizer_model_constraint`](@ref) has been extended correctly and/or [`map_dual`](@ref) has been extended for constraints.

**Example**

```julia-repl
julia> dual(c1)
4-element Array{Float64,1}:
 -42.0
 -42.0
 32.3
 0.0
```
