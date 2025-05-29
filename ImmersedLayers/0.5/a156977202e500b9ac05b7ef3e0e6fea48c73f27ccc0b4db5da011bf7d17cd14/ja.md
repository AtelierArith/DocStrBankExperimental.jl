```
regularize_normal!(qt::EdgeGradient{Primal},v::VectorData,cache::BasicILMCache)
regularize_normal!(qt::EdgeGradient{Primal},v::VectorData,sys::ILMSystem)
```

操作 $\mathbf{q}_t = R_t \mathbf{n}\circ \mathbf{v}$ は、スカラーのベクトルデータ `v`（速度のジャンプのような）をグリッドデータ `qt`（速度-法線テンソルのような）にマッピングします。これは [`normal_interpolate!`](@ref) の随伴です。
