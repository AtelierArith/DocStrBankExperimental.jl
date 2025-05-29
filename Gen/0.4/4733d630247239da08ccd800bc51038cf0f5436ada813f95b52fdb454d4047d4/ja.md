```
@write(<destination>, <value>, <annotation>)
```

ランダムな選択の値を[Trace Transform DSL](@ref)の出力トレースに書き込むためのマクロです。

<destination>は<trace>[<addr>]の形式であり、<trace>は入力トレースで、<annotation>は:discreteまたは:continuousのいずれかです。
