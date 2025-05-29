```
FiniteTimeReachability{VT <: Vector{<:CartesianIndex}, T <: Integer}
```

有限時間到達可能性は、ターゲット/終端状態のセットと時間のホライズンによって指定されます。すなわち、トレースを$s_1 s_2 s_3 \cdots$と表すと、$T$がターゲット状態のセットであり、$H$が時間のホライズンである場合、性質は次のようになります。

$$
    \mathbb{P}(\exists k = \{0, \ldots, H\}, s_k \in T).
$$
