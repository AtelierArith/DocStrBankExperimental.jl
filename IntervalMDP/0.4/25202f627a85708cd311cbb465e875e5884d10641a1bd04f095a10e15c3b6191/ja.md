```
FiniteTimeSafety{VT <: Vector{<:CartesianIndex}, T <: Integer}
```

有限時間安全性は、回避状態の集合と時間の地平線によって指定されます。すなわち、トレースを $s_1 s_2 s_3 \cdots$ と表すと、$A$ が回避状態の集合であり、$H$ が時間の地平線である場合、性質は次のようになります。

$$
    \mathbb{P}(\forall k = \{0, \ldots, H\}, s_k \notin A).
$$
