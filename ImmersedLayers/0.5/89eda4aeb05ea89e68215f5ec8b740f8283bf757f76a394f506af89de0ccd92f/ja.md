```
curl!(v::Edges{Primal},s::Nodes{Dual},cache::BasicILMCache)
curl!(v::Edges{Primal},s::Nodes{Dual},sys::ILMSystem)
```

`s`の離散的なカールを計算し、`v`に返します。`cache`（または`sys`）が`GridScaling`型の場合はグリッド間隔でスケーリングし、`cache`（または`sys`）が`IndexScaling`型の場合は単純な差分として残します。
