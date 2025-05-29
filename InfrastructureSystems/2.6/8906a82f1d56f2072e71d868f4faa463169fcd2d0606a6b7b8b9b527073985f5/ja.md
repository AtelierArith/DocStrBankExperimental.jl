```julia
rebuild_selector(
    selector::InfrastructureSystems.DynamicallyGroupedComponentSelector;
    name,
    groupby
) -> Any

```

入力された `selector` と機能的に同一の [`ComponentSelector`](@ref) を返しますが、キーワード引数で指定されたフィールドの変更が含まれます。

# 例

`groupby = :all` のセレクタがあるとします。代わりに `groupby = :each` を希望する場合：

```julia
sel = make_selector(ThermalStandard; groupby = :all)
sel_each = rebuild_selector(sel; groupby = :each)
```
