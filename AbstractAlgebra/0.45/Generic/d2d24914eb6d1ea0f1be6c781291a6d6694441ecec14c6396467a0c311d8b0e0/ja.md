```
evaluate(a::U, vars::Vector{Int}, vals::Vector{U}) where {T <: RingElement, U <: AbsMSeries{T}}
```

指定された値を配列 `vals` から対応する変数に対して置き換えることによって、系列式を評価します。値は $a$ と同じ環に属している必要があります。
