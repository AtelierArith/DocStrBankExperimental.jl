```
curl!(w::Nodes{Dual},v::Edges{Primal},cache::BasicILMCache)
curl!(w::Nodes{Dual},v::Edges{Primal},sys::ILMSystem)
```

`v` の離散的なカールを計算し、`w` に返します。`cache`（または `sys`）が `GridScaling` 型の場合はグリッド間隔でスケーリングし、`cache`（または `sys`）が `IndexScaling` 型の場合は単純な差分として残します。
