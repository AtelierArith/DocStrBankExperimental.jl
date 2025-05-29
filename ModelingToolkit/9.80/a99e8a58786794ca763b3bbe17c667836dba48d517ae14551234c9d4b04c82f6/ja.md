```julia
toggle_namespacing(
    sys::ModelingToolkit.AbstractSystem,
    value::Bool;
    safe
) -> Any

```

`sys`の名前空間を有効または無効にした新しい`sys`を返します。これは`value`に依存します。キーワード引数`safe`は、そのようなトグルをサポートしないシステムがエラーを出すべきか無視されるべきかを示します。
