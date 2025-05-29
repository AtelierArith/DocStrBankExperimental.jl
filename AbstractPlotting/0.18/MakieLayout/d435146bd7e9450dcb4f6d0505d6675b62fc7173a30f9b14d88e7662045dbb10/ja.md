```
labelslider!(scene, label, range; format = string, sliderkw = Dict(), labelkw = Dict(), valuekw = Dict(), layoutkw...)
```

`scene`にラベル、スライダー、値ラベルを持つ水平のGridLayoutを構築します。

`NamedTuple`を返します：

`(slider = slider, label = label, valuelabel = valuelabel, layout = layout)`

`format`キーワードを使用して値ラベルのフォーマット関数を指定します。スライダーには`sliderkw`からキーワードが渡されます。ラベルには`labelkw`からキーワードが渡されます。値ラベルには`valuekw`からキーワードが渡されます。その他のキーワードは`GridLayout`に渡されます。

例：

```
ls = labelslider!(scene, "Voltage:", 0:10; format = x -> "$(x)V")
layout[1, 1] = ls.layout
```
