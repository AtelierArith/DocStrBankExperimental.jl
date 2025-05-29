```
InfiniteOpt.expression_supports(model::JuMP.Model,
    expr::JuMP.AbstractJuMPScalar,
    key::Val{:TransData} = Val(:TransData);
    [label::Type{<:InfiniteOpt.AbstractSupportLabel} = InfiniteOpt.PublicLabel,
    ndarray::Bool = false])
```

`expr` に関連付けられたサポートエイリアスマッピングを返します。`expr` を転写できない場合はエラーが発生します。
