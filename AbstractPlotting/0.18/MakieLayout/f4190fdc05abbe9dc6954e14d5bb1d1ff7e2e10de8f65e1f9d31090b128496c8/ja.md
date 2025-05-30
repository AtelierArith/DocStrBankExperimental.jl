```
labelslidergrid!(scene, labels, ranges; formats = [string],
    sliderkw = Dict(), labelkw = Dict(), valuekw = Dict(), layoutkw...)
```

`scene`にラベルの列、スライダーの列、値ラベルの列を持つGridLayoutを構築します。引数の値はブロードキャストされるため、ラベル、範囲、またはフォーマットを行ごとに一定に保ちたい場合はスカラーを使用できます。

`NamedTuple`を返します：

`(sliders = sliders, labels = labels, valuelabels = valuelabels, layout = layout)`

`formats`キーワードを使用して値ラベルのフォーマット関数を指定します。スライダーには`sliderkw`からのキーワードが渡されます。ラベルには`labelkw`からのキーワードが渡されます。値ラベルには`valuekw`からのキーワードが渡されます。その他のキーワードは`GridLayout`に渡されます。

例：

```
ls = labelslidergrid!(scene, ["Voltage", "Ampere"], Ref(0:0.1:100); format = x -> "$(x)V")
layout[1, 1] = ls.layout
```
