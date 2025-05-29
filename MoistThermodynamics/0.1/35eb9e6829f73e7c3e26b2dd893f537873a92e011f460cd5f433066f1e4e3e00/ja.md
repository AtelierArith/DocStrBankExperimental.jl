```
liquid_fraction(T[, q::PhasePartition])
```

液体の割合は、以下の条件で液体の凝縮物の割合です。

  * `T` 温度
  * `q` [`PhasePartition`](@ref)

`q.liq` または `q.ice` が非ゼロの場合、液体の割合はそれらから計算されます。

そうでない場合、相平衡が仮定され、液体の割合は `T_freeze` より上では 1 で、`T_freeze` より下では 0 になります。
