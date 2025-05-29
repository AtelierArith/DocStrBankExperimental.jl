`tabulator(options::AbstractDict; index, key)`

オプションのキーをラベルとするトグルボタンのセットを作成します。選択されたオプションの値をその下に表示します。`index::Int`を使用して初期オプションのインデックスを選択するか、`key::String`を使用します。出力は選択された`index`です。選択されたオプションがない場合は`index=0`を使用します。

## 例

```julia
tabulator(OrderedDict("plot" => plot(rand(10)), "scatter" => scatter(rand(10))), index = 1)
tabulator(OrderedDict("plot" => plot(rand(10)), "scatter" => scatter(rand(10))), key = "plot")
```

`tabulator(values::AbstractArray; kwargs...)`

ラベル`values`を持つ`tabulator`。詳細については`tabulator(options::AbstractDict; ...)`を参照してください。

```
tabulator(options::Observable; navbar=tabs, kwargs...)
```

与えられた`Observable`をオプションとするタブレーター。`Observable`を他の値に設定すると、リアルタイムでオプションが更新されます。デフォルトは`navbar=tabs`です：ボタンの代わりにタブを使用するには`navbar=togglebuttons`を使用します。

## 例

```julia
options = Observable(["a", "b", "c"])
wdg = tabulator(options)
options[] = ["c", "d", "e"]
```

`options`はウィジェットから直接変更できます：

```julia
wdg[:options][] = ["c", "d", "e"]
```
