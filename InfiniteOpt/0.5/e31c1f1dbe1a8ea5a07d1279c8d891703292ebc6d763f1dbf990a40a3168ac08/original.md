```
optimizer_model_constraint(cref::InfOptConstraintRef; 
                           [label::Type{<:AbstractSupportLabel} = PublicLabel, 
                           ndarray::Bool = false,
                           kwargs...])
```

Return the reformulation constraint(s) stored in the optimizer model that correspond to `cref`. Errors if no such constraint can be found in the optimizer model.

The keyword arugments `label` and `ndarray` are what `TranscriptionOpt` employ  and `kwargs` denote extra ones that user extensions may employ in accordance with their implementation of [`optimizer_model_constraint`](@ref). Errors if such an extension has not been written. 

By default only the constraints associated with public supports are returned, the  full set can be accessed via `label = All`. Moreover, infinite constraints are  returned as a list corresponding to their supports. However, a n-dimensional array  can be obtained via `ndarray = true` which is handy when the constraint has multiple  infinite parameter dependencies. The corresponding supports are obtained via  `supports` using the same keyword arguments.

**Example**

```julia-repl
julia> optimizer_model_constraint(c1) # finite constraint
c1 : x(support: 1) - y <= 3.0
```
