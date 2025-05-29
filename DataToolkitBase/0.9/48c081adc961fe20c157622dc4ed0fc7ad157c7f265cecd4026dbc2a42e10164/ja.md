```
supportedtypes(ADT::Type{<:AbstractDataTransformer})::Vector{QualifiedType}
```

データ変換器 `ADT` によってサポートされている型のリストを返します。

これは、Data TOML の `type` キーのデフォルト値として使用されます。型のリストは、データ変換器の利用可能なメソッドに基づいて動的に生成されます。

場合によっては、特定の変換器のためにこれを明示的に定義することが理にかなうことがあります。
