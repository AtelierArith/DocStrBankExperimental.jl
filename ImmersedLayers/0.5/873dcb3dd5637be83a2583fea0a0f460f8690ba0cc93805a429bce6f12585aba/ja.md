```
regularize_normal_cross!(v::Edges{Primal},f::ScalarData,cache::BasicILMCache)
regularize_normal_cross!(v::Edges{Primal},f::ScalarData,sys::ILMSystem)
```

操作 $\mathbf{v} = R_f \mathbf{n}\times f \mathbf{e}_z$ は、スカラー表面データ `f`（流れ関数のジャンプのようなもので、面外単位ベクトル $\mathbf{e}_z$ を持つ）をグリッドデータ `v`（速度のようなもの）にマッピングします。これは [`normal_cross_interpolate!`](@ref) の負の随伴です。
