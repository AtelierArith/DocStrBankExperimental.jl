```
InfiniteOpt.optimizer_model_variable(vref::InfiniteOpt.GeneralVariableRef,
    ::Val{:TransData};
    [label::Type{<:InfiniteOpt.AbstractSupportLabel} = InfiniteOpt.PublicLabel,
    ndarray::Bool = false])
```

Proper extension of [`InfiniteOpt.optimizer_model_variable`](@ref) for `TranscriptionModel`s. This simply dispatches to [`transcription_variable`](@ref).
