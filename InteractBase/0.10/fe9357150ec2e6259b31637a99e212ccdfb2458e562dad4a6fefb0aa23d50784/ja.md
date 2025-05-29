```
toggles(options::AbstractDict;
         value = first(values(options)))
```

オプションのキーがアイテムラベルであるトグルスイッチのリスト。observableは、選択されたすべてのアイテムの値を含む配列を保持します。例: `toggles(OrderedDict("good"=>1, "better"=>2, "amazing"=>9001))`

`toggles(values::AbstractArray; kwargs...)`

`toggles`は`string.(values)`というラベルを持ちます。詳細については`toggles(options::AbstractDict; ...)`を参照してください。

```
toggles(options::AbstractObservable; kwargs...)
```

`options`が指定された`Observable`であるトグル。`Observable`を他の値に設定すると、リアルタイムでオプションが更新されます。

## 例

```julia
options = Observable(["a", "b", "c"])
wdg = toggles(options)
options[] = ["c", "d", "e"]
```

`options`はウィジェットから直接変更できます:

```julia
wdg[:options][] = ["c", "d", "e"]
```
