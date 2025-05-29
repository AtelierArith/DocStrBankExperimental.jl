```
backgroundpoints(layer::T, n::Int; kwargs...) where {T <: SimpleSDMLayer}
```

レイヤーに基づいて背景ポイントを生成します。このレイヤーは最終サンプル内の各セルの重みを提供します。追加のキーワード引数は内部で使用される `StatsBase.sample` に渡されます。これには、サンプリングが置換を使用するかどうかを決定するための `replace` キーワードが含まれます。
