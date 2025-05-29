```
InfiniteOpt.optimizer_model_expression(expr::JuMP.AbstractJuMPScalar,
    ::Val{:TransData};
    [label::Type{<:InfiniteOpt.AbstractSupportLabel} = InfiniteOpt.PublicLabel,
    ndarray::Bool = false])
```

[`InfiniteOpt.optimizer_model_expression`](@ref) の `TranscriptionModel` に対する適切な拡張。これは単に [`transcription_expression`](@ref) にディスパッチします。
