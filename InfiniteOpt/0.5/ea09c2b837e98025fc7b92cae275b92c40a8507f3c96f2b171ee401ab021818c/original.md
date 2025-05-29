```
supports(expr::JuMP.AbstractJuMPScalar; 
         [label::Type{<:AbstractSupportLabel} = PublicLabel,
         ndarray::Bool = false,
         kwargs...])
```

Return the support associated with `expr`. Errors if `expr` is not associated with the constraint mappings stored in `optimizer_model`.

The keyword arugments `label` and `ndarray` are what `TranscriptionOpt` employ  and `kwargs` denote extra ones that user extensions may employ in accordance with their implementation of `expression_supports`. Errors if such an extension has not been written. 

By default only the public supports are returned, the  full set can be accessed via `label = All`. Moreover, the supports of infinite  expressions are returned as a list. However, a n-dimensional array  can be obtained via `ndarray = true` which is handy when the expression has multiple  infinite parameter dependencies.

**Example**

```julia-repl
julia> supports(cref)
2-element Array{Tuple{Float64},1}:
 (0.0,)
 (1.0,)
```
