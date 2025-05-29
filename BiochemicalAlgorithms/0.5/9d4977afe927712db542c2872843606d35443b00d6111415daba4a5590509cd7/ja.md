```julia
get_property(
    ac::BiochemicalAlgorithms.AbstractSystemComponent,
    key::Symbol,
    default
) -> Any

```

指定されたキーに関連付けられたプロパティを `ac` から返します。該当するプロパティが存在しない場合は、`default` を返します。
