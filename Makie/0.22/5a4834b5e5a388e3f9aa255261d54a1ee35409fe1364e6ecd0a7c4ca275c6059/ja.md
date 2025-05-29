```
labelslider!(scene, label, range; format = string, sliderkw = Dict(),
labelkw = Dict(), valuekw = Dict(), value_column_width = automatic, layoutkw...)
```

**`labelslider!`は非推奨です。代わりに`SliderGrid`を使用してください。**

`scene`内にラベル、スライダー、値ラベルを持つ水平のGridLayoutを構築します。

`NamedTuple`を返します：

`(slider = slider, label = label, valuelabel = valuelabel, layout = layout)`

`format`キーワードを使用して値ラベルのフォーマット関数を指定するか、`Format.format`で使用されるフォーマット文字列を渡します。スライダーには`sliderkw`からキーワードが転送されます。ラベルには`labelkw`からキーワードが転送されます。値ラベルには`valuekw`からキーワードが転送されます。値ラベル列の列幅は`value_column_width`キーワードで設定できます。デフォルトでは、幅はスライダー範囲からいくつかの値をサンプリングしてヒューリスティックに決定されます。他のすべてのキーワードは`GridLayout`に転送されます。

例：

```julia
ls = labelslider!(scene, "Voltage:", 0:10; format = x -> "$(x)V")
layout[1, 1] = ls.layout
```
