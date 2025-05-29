```
InfiniteOpt.optimizer_model_constraint(
    cref::InfiniteOpt.InfOptConstraintRef,
    ::Val{:TransData};
    [label::Type{<:InfiniteOpt.AbstractSupportLabel} = InfiniteOpt.PublicLabel
    ndarray::Bool = false])
```

Proper extension of [`InfiniteOpt.optimizer_model_constraint`](@ref) for `TranscriptionModel`s. This simply dispatches to [`transcription_constraint`](@ref).
