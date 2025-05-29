```
FuncTransform(sig, world, fargs::Union{Vector{FuncArgs}, Nothing} = nothing;
    caller::Union{MethodInstance, Nothing} = nothing,
    method_tables::Union{Nothing, MethodTable} = nothing)
```

`FuncTransform`オブジェクトを構築し、世界の年齢`world`の関数`sig`に対して変換を実行します。`fargs`は新しい関数の新しい引数を指定するために使用されます。`fargs`が`nothing`の場合、元の引数が使用されます。`caller`が提供されると、バックエッジもそれに応じて設定されます。変換は`FuncTransform(...).fi::FuncInfo`に適用され、結果を得るために`toCodeInfo`を使用します。
