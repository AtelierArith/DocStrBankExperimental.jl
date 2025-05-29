```
saturation_excess(T, ρ, q::PhasePartition)
```

平衡状態における飽和過剰は次のように定義されます。

  * `T` 温度
  * `ρ` （湿）空気密度
  * `q` [`PhasePartition`](@ref)

飽和過剰は、全特定湿度 `q.tot` と平衡状態における飽和特定湿度との違いであり、この違いが正である場合にのみ非ゼロと定義されます。
