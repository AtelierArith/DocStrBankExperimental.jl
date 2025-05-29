```
itemplot(model, item, args...; kwargs...)
```

`model`の`item`のアイテムプロットを作成します。

結果として得られるアイテムプロットには、アイテム特性曲線（左）とアイテム情報曲線（右）が含まれます。

追加の`args...`と`kwargs...`は、下位レベルの関数[`item_characteristic_curve`](@ref)および[`item_information_curve`](@ref)に渡されます。
