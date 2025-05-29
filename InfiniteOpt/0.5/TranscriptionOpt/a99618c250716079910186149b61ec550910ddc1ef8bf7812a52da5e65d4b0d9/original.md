```
InfiniteOpt.optimizer_model_expression(expr::JuMP.AbstractJuMPScalar,
    ::Val{:TransData};
    [label::Type{<:InfiniteOpt.AbstractSupportLabel} = InfiniteOpt.PublicLabel,
    ndarray::Bool = false])
```

Proper extension of [`InfiniteOpt.optimizer_model_expression`](@ref) for `TranscriptionModel`s. This simply dispatches to [`transcription_expression`](@ref).
