```
simdgroup_barrier(flag::MemoryFlags=MemoryFlagNone)
```

SIMDグループ内のすべてのスレッドを同期します。

メモリ同期の動作に影響を与える可能性のあるフラグは[`MemoryFlags`](@ref)にあります。
