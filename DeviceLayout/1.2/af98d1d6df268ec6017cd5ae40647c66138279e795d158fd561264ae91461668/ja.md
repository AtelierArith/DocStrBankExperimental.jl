```
render!(cell::Cell{S}, cs::GeometryStructure;
    memoized_cells=Dict{CoordinateSystem, Cell}(),
    map_meta = identity,
    kwargs...) where {S}
```

ジオメトリ構造（例：`CoordinateSystem`）をセルにレンダリングします。

各要素とそのメタデータ（メソッドが提供されている場合は`map_meta`によってマッピングされる）を`render!(::Cell, element, ::Meta)`に渡し、参照をたどります。これにより、`CoordinateSystem`が複数の場所で参照されている場合、それは複数の場所で参照される単一のセルになります。

`GeometryEntity`を`Cell`にレンダリングする際には、オプションのキーワード引数を使用します。

  * `map_meta`は、`Meta`オブジェクトを受け取り、別の`Meta`オブジェクト（または`nothing`、この場合はレンダリングがスキップされます）を返す関数です。

使用上の注意：非空の辞書`memoized_cells = Dict{CoordinateSystem, Cell}(cs => cell)`を使用してこの関数を呼び出すことは、実質的に手動のオーバーライドであり、`cs`を`cell`としてレンダリングすることを強制します。
