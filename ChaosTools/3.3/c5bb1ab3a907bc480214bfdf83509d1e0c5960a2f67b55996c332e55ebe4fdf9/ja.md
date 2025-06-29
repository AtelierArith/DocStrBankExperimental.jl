```
first_return_times(ds::DynamicalSystem, u0, εs, T; diffeq = NamedTuple(), kwargs...) → t
```

与えられた力学系に対して、半径 `εs` の `u0` を中心とした集合への最初の帰還時間 `t` を返します。`ds` の時間発展は常に `u0` から始まります。

この関数は [`exit_entry_times`](@ref) と同じ原則で動作するため、`u0, εs` に関する詳細はそのドキュメントを参照してください。ここでの唯一の違いは次のとおりです：

1. システムが時間 `T` 内に集合に戻らなかった場合、`0` が返されます。
2. 連続システムの場合、正確に返される時間は時間発展の開始から、`u0` に最も近づくまでの時間であり、これは少なくとも `ε`-近い場合に限ります。
