```
evaluate(a::U, vars::Vector{Int}, vals::Vector{U}) where {T <: RingElement, U <: AbsMSeries{T}}
```

指定された配列 `vals` の値を、配列 `vars` で与えられたインデックスの対応する変数に代入することによって、系列式を評価します。値は $a$ と同じ環に属している必要があります。
