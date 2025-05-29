`tabs(options::AbstractDict; value::Union{T, Observable})`

オプションのキーがラベルであるタブのセットを作成します。ラベルはリンクであることができます。

`tabs(values::AbstractArray; kwargs...)`

ラベルが`values`の`tabs`。詳細については`tabs(options::AbstractDict; ...)`を参照してください。

```
tabs(options::AbstractObservable; kwargs...)
```

与えられた`Observable`の`options`を持つタブ。`Observable`を他の値に設定すると、リアルタイムでオプションが更新されます。

## 例

```julia
options = Observable(["a", "b", "c"])
wdg = tabs(options)
options[] = ["c", "d", "e"]
```

`options`はウィジェットから直接変更できます：

```julia
wdg[:options][] = ["c", "d", "e"]
```
