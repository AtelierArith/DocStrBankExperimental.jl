```
checkboxes(options::AbstractDict;
         value = valtype(options)[]
```

オプションのキーがアイテムラベルであるチェックボックスのリスト。選択されたすべてのアイテムの値を含む配列を保持するobservable、例: `checkboxes(OrderedDict("good"=>1, "better"=>2, "amazing"=>9001))`

`checkboxes(values::AbstractArray; kwargs...)`

`checkboxes`はラベル`string.(values)`を持ちます。詳細については`checkboxes(options::AbstractDict; ...)`を参照してください。

```
checkboxes(options::AbstractObservable; kwargs...)
```

`options`が指定された`Observable`であるチェックボックス。`Observable`を他の値に設定して、リアルタイムでオプションを更新します。

## 例

```julia
options = Observable(["a", "b", "c"])
wdg = checkboxes(options)
options[] = ["c", "d", "e"]
```

`options`はウィジェットから直接変更できます：

```julia
wdg[:options][] = ["c", "d", "e"]
```

表示時にすでにチェックが入っているチェックボックスを作成するには、`value`キーワードを使用します：

```julia
options = ["a", "b", "c"]
value = ["a", "c"]
checkboxes(options, value = value)
```

チェックボックスウィジェットが表示されると、"a"と"c"のボックスにチェックが入ります。`options`と`value`の両方がObservablesであることができます。
