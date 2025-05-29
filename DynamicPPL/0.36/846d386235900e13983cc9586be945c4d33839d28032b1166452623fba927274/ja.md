```
VarInfo([rng, ]model[, sampler, context])
```

指定された `model` のために `VarInfo` オブジェクトを生成します。これは、指定された `rng`、`sampler`、および `context` を使用して一度評価することによって行われます。

!!! warning
    この関数は現在、メタデータフィールドが `Metadata` の `NamedTuple` に設定された `VarInfo` を返します。これは実装の詳細です。一般的に、この関数は `AbstractVarInfo` インターフェースを満たすすべての種類のオブジェクトを返す可能性があります。返される `VarInfo` の型を正確に制御する必要がある場合は、内部関数 `untyped_varinfo`、`typed_varinfo`、`untyped_vector_varinfo`、または `typed_vector_varinfo` を代わりに使用してください。

