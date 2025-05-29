```
dropdown(options::AbstractObservable;
         value = first(values(options[])),
         label = nothing,
         multiple = false)
```

与えられた `Observable` の `options` を持つドロップダウンメニュー。`Observable` を他の値に設定すると、リアルタイムでオプションが更新されます。

## 例

```julia
options = Observable(["a", "b", "c"])
wdg = dropdown(options)
options[] = ["c", "d", "e"]
```

`options` はウィジェットから直接変更することもできます：

```julia
wdg[:options][] = ["c", "d", "e"]
```
