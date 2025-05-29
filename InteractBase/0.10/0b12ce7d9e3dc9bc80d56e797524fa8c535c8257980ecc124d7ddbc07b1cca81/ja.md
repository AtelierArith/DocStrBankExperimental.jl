`togglebuttons(options::AbstractDict; value::Union{T, Observable}, multiple=false)`

オプションのキーがラベルのトグルボタンのセットを作成します。`multiple=true`を設定すると、同時に複数（またはゼロ）のアクティブボタンを許可します。

`togglebuttons(values::AbstractArray; kwargs...)`

ラベルが`string.(values)`の`togglebuttons`です。詳細については`togglebuttons(options::AbstractDict; ...)`を参照してください。

```
togglebuttons(options::AbstractObservable; kwargs...)
```

与えられた`Observable`の`options`を持つトグルボタンです。`Observable`を他の値に設定すると、リアルタイムでオプションが更新されます。

## 例

```julia
options = Observable(["a", "b", "c"])
wdg = togglebuttons(options)
options[] = ["c", "d", "e"]
```

`options`はウィジェットから直接変更できます：

```julia
wdg[:options][] = ["c", "d", "e"]
```
