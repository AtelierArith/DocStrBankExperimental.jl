```julia
toggle_namespacing(
    sys::ModelingToolkit.AbstractSystem,
    value::Bool;
    safe
) -> Any

```

`value`に応じて、名前空間が有効または無効になった新しい`sys`を返します。キーワード引数`safe`は、そのようなトグルをサポートしないシステムがエラーを出すべきか無視されるべきかを示します。
