```
ShannonExtropy <: InformationMeasure
ShannonExtropy(; base = 2)
```

シャノンエントロピー [Lad2015](@cite) は、確率分布 $P = \{p_1, p_2, \ldots, p_N\}$ に対して、[`information`](@ref) と共に計算するために使用されます。

$$
J(x) = -\sum_{i=1}^N (1 - p[i]) \log{(1 - p[i])},
$$

ここで、$\log$ は指定された `base` で計算されます。
