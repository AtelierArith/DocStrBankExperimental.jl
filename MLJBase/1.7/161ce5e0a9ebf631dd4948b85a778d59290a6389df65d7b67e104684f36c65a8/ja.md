```
fit!(N::Node;
     rows=nothing,
     verbosity=1,
     force=false,
     acceleration=CPU1())
```

ノード `N` を呼び出すために必要なすべてのマシンを適切な順序でトレーニングしますが、指定された `acceleration` モードを使用して可能な限り並列化します。これらのマシンは `machines(N)` によって返されます。

サポートされている `acceleration` モード: `CPU1()`, `CPUThreads()`。
