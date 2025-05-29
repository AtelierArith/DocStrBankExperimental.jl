```julia
numa_bitmask_alloc() -> NUMA.Bitmask
numa_bitmask_alloc(n::Integer) -> NUMA.Bitmask

```

ビットマスク構造体とその関連ビットマスクを割り当てます。ビットマスクのために割り当てられたメモリは、`n` ビットを含むのに十分なワード（型 `UInt64`）を含みます。`n` が提供されていない場合、`nnumanodes()` が使用されます。

ビットマスクはゼロで埋められています。
