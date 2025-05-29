```
labelslidergrid!(scene, labels, ranges; formats = [string],
    sliderkw = Dict(), labelkw = Dict(), valuekw = Dict(),
    value_column_width = automatic, layoutkw...)
```

**`labelslidergrid!` は非推奨です。代わりに `SliderGrid` を使用してください。**

`scene` にラベルの列、スライダーの列、値ラベルの列を持つ GridLayout を構築します。引数の値はブロードキャストされるため、スカラーを使用してラベル、範囲、またはフォーマットを行の間で一定に保つことができます。

`NamedTuple` を返します：

`(sliders = sliders, labels = labels, valuelabels = valuelabels, layout = layout)`

値ラベルのフォーマット関数を `formats` キーワードで指定するか、`Format.format` で使用されるフォーマット文字列を渡します。スライダーには `sliderkw` からのキーワードが渡されます。ラベルには `labelkw` からのキーワードが渡されます。値ラベルには `valuekw` からのキーワードが渡されます。値ラベル列の列幅は `value_column_width` キーワードで設定できます。デフォルトでは、幅はスライダー範囲からいくつかの値をサンプリングしてヒューリスティックに決定されます。他のすべてのキーワードは `GridLayout` に渡されます。

例：

```julia
ls = labelslidergrid!(scene, ["Voltage", "Ampere"], Ref(0:0.1:100); format = x -> "$(x)V")
layout[1, 1] = ls.layout
```
