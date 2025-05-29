```
oneof_field_types(::Type{T}) where T
```

`oneof` フィールド名から、個々の `oneof` オプションの型を説明する完全な NamedTuple 型への名前付きタプルを返します。元の proto メッセージに `oneof` フィールドが含まれていない場合は、空の名前付きタプル `(;)` を返します。
