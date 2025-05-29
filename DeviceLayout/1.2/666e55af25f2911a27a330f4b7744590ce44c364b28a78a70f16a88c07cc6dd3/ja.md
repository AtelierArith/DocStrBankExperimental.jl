```
flatten(c::GeometryReference; depth::Integer=-1, name=uniquename("flatten_"*name(structure(c))), metadata_filter=nothing)
```

新しい構造体を返します。名前は `name` で、階層的な `depth` まで再帰的にフラット化された参照と配列を持っています。

フラット化は、参照の要素を適切な変換を伴って最上位の座標系に追加し、その後それらの参照を破棄します。より深い参照と配列は持ち上げられ、破棄されません。`depth=0` の場合、新しい座標系が返され、参照のみが含まれます。

`metadata_filter` は `DeviceLayout.Meta` を受け取り、`Bool` を返す関数である可能性があります。これは [`layer_inclusion`](@ref) によって返される関数のようなものです。その場合、メタデータ `m` が `metadata_filter(m) == true` である要素のみがフラット化中に保持されます。より深い参照と配列の要素はフィルタリングされません。

参照 `c` は変更されません。
