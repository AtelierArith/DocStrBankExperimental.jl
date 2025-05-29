```julia
make_transform(V; ...)
make_transform(V, input; kwargs...)

```

指定されたキーワード引数 `kwargs` に従って提供された `input` プロトタイプ配列に適用できる変換演算子（`transformOp(V)` によって与えられる）を持つ `V` のコピーを返します。
