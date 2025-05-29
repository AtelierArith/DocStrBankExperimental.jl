```
InfiniteOpt.constraint_supports(model::JuMP.Model,
    cref::InfiniteOpt.InfOptConstraintRef,
    key::Val{:TransData} = Val(:TransData);
    [label::Type{<:InfiniteOpt.AbstractSupportLabel} = InfiniteOpt.PublicLabel,
    ndarray::Bool = false])
```

Return the support alias mappings associated with `cref`. Errors if `cref` is not transcribed.
