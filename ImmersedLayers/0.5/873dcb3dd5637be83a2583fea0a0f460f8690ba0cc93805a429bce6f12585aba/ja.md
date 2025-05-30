```
regularize_normal_cross!(v::Edges{Primal},f::ScalarData,cache::BasicILMCache)
regularize_normal_cross!(v::Edges{Primal},f::ScalarData,sys::ILMSystem)
```

操作 $\mathbf{v} = R_f \mathbf{n}\times f \mathbf{e}_z$ は、スカラー表面データ `f`（面外単位ベクトル $\mathbf{e}_z$ を持つ流れ関数のジャンプのようなもの）をグリッドデータ `v`（速度のようなもの）にマッピングします。これは [`normal_cross_interpolate!`](@ref) の負随伴です。
