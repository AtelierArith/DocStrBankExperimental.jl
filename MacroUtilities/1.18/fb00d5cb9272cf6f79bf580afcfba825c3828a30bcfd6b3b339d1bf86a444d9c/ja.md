```
kwarg_constructor(typename, fields::Vector{TypedVar}, default_vals; [lnn::Union{LineNumberNode, Nothing)=nothing], [whereparams=not_provided])
```

`typename`のための`fields`を持つ`FuncDef`キーワード引数コンストラクタを返し、`default_vals`は`Base.get(default_vals, fieldname, default)`を実装する任意のコレクションです。
