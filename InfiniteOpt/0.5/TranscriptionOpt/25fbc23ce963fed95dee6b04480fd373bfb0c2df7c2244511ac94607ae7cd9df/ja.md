```
InfiniteOpt.optimizer_model_constraint(
    cref::InfiniteOpt.InfOptConstraintRef,
    ::Val{:TransData};
    [label::Type{<:InfiniteOpt.AbstractSupportLabel} = InfiniteOpt.PublicLabel
    ndarray::Bool = false])
```

[`InfiniteOpt.optimizer_model_constraint`](@ref) の `TranscriptionModel` に対する適切な拡張。これは単に [`transcription_constraint`](@ref) にディスパッチします。
