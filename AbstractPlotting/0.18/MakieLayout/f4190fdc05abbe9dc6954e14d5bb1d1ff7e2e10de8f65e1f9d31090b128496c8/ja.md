```
labelslidergrid!(scene, labels, ranges; formats = [string],
    sliderkw = Dict(), labelkw = Dict(), valuekw = Dict(), layoutkw...)
```

`scene`にラベルの列、スライダーの列、値ラベルの列を持つGridLayoutを構築します。引数の値はブロードキャストされるため、スカラーを使用してラベル、範囲、またはフォーマットを行ごとに一定に保つことができます。

`NamedTuple`を返します：

`(sliders = sliders, labels = labels, valuelabels = valuelabels, layout = layout)`

`formats`キーワードを使用して値ラベルのフォーマット関数を指定します。スライダーには`sliderkw`からキーワードが渡されます。ラベルには`labelkw`からキーワードが渡されます。値ラベルには`valuekw`からキーワードが渡されます。その他のすべてのキーワードは`GridLayout`に渡されます。

例：

```
ls = labelslidergrid!(scene, ["Voltage", "Ampere"], Ref(0:0.1:100); format = x -> "$(x)V")
layout[1, 1] = ls.layout
```
