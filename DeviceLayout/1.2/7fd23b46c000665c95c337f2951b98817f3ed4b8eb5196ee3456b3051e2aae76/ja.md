```
flatten(c::GeometryStructure; depth::Integer=-1, name=uniquename("flatten_"*name(c)), metadata_filter=nothing)
```

新しい座標系を名前 `name` で返し、階層的な `depth` まで再帰的に参照と配列をフラット化します。

`CoordinateSystem` または `Cell` をフラット化すると、同じタイプの座標系が生成されます（つまり、これらは [`flatten!`](@ref) を使ってインプレースでフラット化することもできます）が、他の構造をフラット化すると、一般的に同じ座標タイプの `CoordinateSystem` が生成されます。

フラット化は、適切な変換を伴って参照の要素を最上位構造に追加し、その後それらの参照を破棄します。より深い参照と配列は持ち上げられ、破棄されることはありません。

`metadata_filter` は `DeviceLayout.Meta` を受け取り `Bool` を返す関数である可能性があり、[`layer_inclusion`](@ref) によって返される関数のようなものです。その場合、メタデータ `m` が `metadata_filter(m) == true` である要素のみがフラット化中に保持されます。より深い参照と配列の要素はフィルタリングされません。

この関数は `depth == 0` の場合には効果がなく、デフォルトでは無制限の深さです。
