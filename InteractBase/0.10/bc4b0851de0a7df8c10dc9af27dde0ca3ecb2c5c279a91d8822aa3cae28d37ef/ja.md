```
radiobuttons(options::AbstractDict;
             value::Union{T, Observable} = first(values(options)))
```

例: `radiobuttons(OrderedDict("good"=>1, "better"=>2, "amazing"=>9001))`

`radiobuttons(values::AbstractArray; kwargs...)`

`radiobuttons` は `string.(values)` のラベルを持ちます。詳細については `radiobuttons(options::AbstractDict; ...)` を参照してください。

```
radiobuttons(options::AbstractObservable; kwargs...)
```

`options` が指定された `Observable` であるラジオボタン。`Observable` を他の値に設定すると、リアルタイムでオプションが更新されます。

## 例

```julia
options = Observable(["a", "b", "c"])
wdg = radiobuttons(options)
options[] = ["c", "d", "e"]
```

`options` はウィジェットから直接変更できます:

```julia
wdg[:options][] = ["c", "d", "e"]
```
