```
InfiniteOpt.constraint_supports(model::JuMP.Model,
    cref::InfiniteOpt.InfOptConstraintRef,
    key::Val{:TransData} = Val(:TransData);
    [label::Type{<:InfiniteOpt.AbstractSupportLabel} = InfiniteOpt.PublicLabel,
    ndarray::Bool = false])
```

`cref` に関連付けられたサポートエイリアスのマッピングを返します。`cref` が転写されていない場合はエラーが発生します。
