```julia
rebuild_selector(
    selector::InfrastructureSystems.ComponentSelector;
    name
) -> InfrastructureSystems.ListComponentSelector

```

入力された `selector` と機能的に同一の [`ComponentSelector`](@ref) を返しますが、キーワード引数で指定されたフィールドの変更が含まれます。

# 例

`name = "my_name"` のセレクタがあるとします。代わりに `name = "your_name"` を希望する場合：

```julia
sel = make_selector(ThermalStandard, "322_CT_6"; name = "my_name")
sel_yours = rebuild_selector(sel; name = "your_name")
```
