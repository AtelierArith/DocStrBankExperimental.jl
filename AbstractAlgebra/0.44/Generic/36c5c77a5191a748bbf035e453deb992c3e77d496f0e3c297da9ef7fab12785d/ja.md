```
evaluate(a::U, vars::Vector{U}, vals::Vector{U}) where {T <: RingElement, U <: AbsMSeries{T}}
```

与えられた配列 `vars` によって指定された変数に対して、配列 `vals` に供給された値を代入することによって、級数式を評価します。値は $a$ と同じ環に属している必要があります。
