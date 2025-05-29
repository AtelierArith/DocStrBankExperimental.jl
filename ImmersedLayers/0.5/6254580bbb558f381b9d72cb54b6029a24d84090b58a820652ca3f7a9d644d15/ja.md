```
regularize_normal_symm!(qt::EdgeGradient{Primal},v::VectorData,cache::BasicILMCache)
regularize_normal_symm!(qt::EdgeGradient{Primal},v::VectorData,sys::ILMSystem)
```

操作 $\mathbf{q}_t = R_t (\mathbf{n}\circ \mathbf{v}+\mathbf{v}\circ \mathbf{n})$ は、スカラー ベクトル データ `v`（速度のジャンプのような）をグリッド データ `qt`（速度-法線テンソルのような）にマッピングします。これは [`normal_interpolate_symm!`](@ref) の随伴です。
