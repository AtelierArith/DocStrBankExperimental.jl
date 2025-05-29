```
WithTypeNames(parent_context)
```

このハッシュコンテキストでは、[`StableHashTraits.transform_type`](@ref) はすべての型に対して [`module_nameof_string`](@ref) を返します。これはデフォルトの動作（主に `nameof_string(StructType(T))` を使用する）とは対照的です。

!!! warn "不安定"
    `module_nameof_string` の返り値は、例えば関数や型のモジュールが変更された場合など、非破壊的な変更によって変わる可能性があります。これはパッケージの実装の詳細と見なされます。

