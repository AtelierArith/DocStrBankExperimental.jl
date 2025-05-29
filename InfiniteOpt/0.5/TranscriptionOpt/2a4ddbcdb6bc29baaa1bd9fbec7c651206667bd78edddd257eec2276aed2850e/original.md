```
InfiniteOpt.expression_supports(model::JuMP.Model,
    expr::JuMP.AbstractJuMPScalar,
    key::Val{:TransData} = Val(:TransData);
    [label::Type{<:InfiniteOpt.AbstractSupportLabel} = InfiniteOpt.PublicLabel,
    ndarray::Bool = false])
```

Return the support alias mappings associated with `expr`. Errors if `expr` cannot be transcribed.
