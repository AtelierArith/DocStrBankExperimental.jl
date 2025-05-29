```
InfiniteOpt.variable_supports(model::JuMP.Model,
    vref::InfiniteOpt.DecisionVariableRef,
    key::Val{:TransData} = Val(:TransData);
    [label::Type{<:InfiniteOpt.AbstractSupportLabel} = InfiniteOpt.PublicLabel,
    ndarray::Bool = false])
```

Return the support alias mapping associated with `vref` in the transcription model. Errors if `vref` does not have transcripted variables. See `transcription_variable`  for an explanation of `ndarray`.
