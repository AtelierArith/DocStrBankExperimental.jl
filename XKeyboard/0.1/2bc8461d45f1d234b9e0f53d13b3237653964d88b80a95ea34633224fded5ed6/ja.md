```
PhysicalKey(keymap::Keymap, name::Symbol)
```

キー マップを使用して、文字列表現 `name` から [`PhysicalKey`](@ref) を取得します。

通常、物理キーの整数コード (keycode) を必要とするイベントをシミュレートするのに便利です。

準備ができている文字列がある場合は、`AbstractString` 型の名前を代わりに使用できます。
