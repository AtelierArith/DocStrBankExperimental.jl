```
InfiniteOpt.variable_supports(model::JuMP.Model,
    vref::InfiniteOpt.DecisionVariableRef,
    key::Val{:TransData} = Val(:TransData);
    [label::Type{<:InfiniteOpt.AbstractSupportLabel} = InfiniteOpt.PublicLabel,
    ndarray::Bool = false])
```

`vref` に関連付けられたサポートエイリアスマッピングを転写モデルから返します。`vref` に転写された変数がない場合はエラーになります。`ndarray` の説明については `transcription_variable` を参照してください。
