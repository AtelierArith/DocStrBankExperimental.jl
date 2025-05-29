```
Cityblock <: Metric
SumAbsoluteDifference <: Metric
cityblock(x, y)
sad(x, y)
```

絶対差の合計（sad）、別名 [`Cityblock`](@ref) 距離は `sum(abs(x - y))` によって計算されます。
