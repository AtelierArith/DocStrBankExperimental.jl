```
InfiniteOpt.optimizer_model_variable(vref::InfiniteOpt.GeneralVariableRef,
    ::Val{:TransData};
    [label::Type{<:InfiniteOpt.AbstractSupportLabel} = InfiniteOpt.PublicLabel,
    ndarray::Bool = false])
```

[`InfiniteOpt.optimizer_model_variable`](@ref) の `TranscriptionModel` に対する適切な拡張。これは単に [`transcription_variable`](@ref) にディスパッチします。
