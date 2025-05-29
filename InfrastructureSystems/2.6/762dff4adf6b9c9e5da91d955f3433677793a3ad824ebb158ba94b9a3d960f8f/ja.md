```julia
rebuild_selector(
    selector::InfrastructureSystems.ListComponentSelector;
    name,
    groupby
) -> InfrastructureSystems.ListComponentSelector

```

入力 `selector` に対して、キーワード引数で指定されたフィールドの変更を除いて、機能的に同一の [`ComponentSelector`](@ref) を返します。結果が同じ具体的な型を持つことは保証されていません。

# 例

手動グループを持つセレクタがあり、`:each` でグループ化したいとします：

```julia
sel = make_selector(make_selector(ThermalStandard), make_selector(RenewableDispatch))
sel_each = rebuild_selector(sel; groupby = :each)  # RegroupedComponentSelector になります
```
