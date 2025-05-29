```
closest_registered_logger(h::HierarchicalLogger{T}, key) -> T
```

もし `haskey(h, key)` が真であれば、`key` に関連付けられたロガーを返します。

そうでなければ、`L ∈ h` のロガーを返します。そのロガーの関連付けられたキー `K` は `startswith(key, K)` を満たし、`L` のキーは `h` のすべてのそのようなロガーの中で最大の長さを持ちます。
