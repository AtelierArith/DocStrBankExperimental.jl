```
divergence!(p::Nodes{Primal/Dual},v::Edges{Primal/Dual},cache::BasicILMCache)
divergence!(p::Nodes{Primal/Dual},v::Edges{Primal/Dual},sys::ILMSystem)
```

`v` の離散的な発散を計算し、`p` に返します。`cache`（または `sys`）が `GridScaling` 型の場合はグリッド間隔でスケーリングし、`cache`（または `sys`）が `IndexScaling` 型の場合は単純な差分として残します。
