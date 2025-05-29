```
evaluate(a::U, vals::Vector{U}) where {T <: RingElement, U <: AbsMSeries{T}}
```

系列式を評価するには、$a$ が属する系列環の変数に対して、配列 `vals` に供給された値を代入します。値は $a$ と同じ環に属している必要があります。
