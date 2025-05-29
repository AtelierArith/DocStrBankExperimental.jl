```
threadgroup_barrier(flag::MemoryFlags=MemoryFlagNone)
```

スレッドグループ内のすべてのスレッドを同期します。

メモリ同期の動作に影響を与える可能性のあるフラグは[`MemoryFlags`](@ref)にあります。
