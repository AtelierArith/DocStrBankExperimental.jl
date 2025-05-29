```
regularize_normal!(v::Edges{Primal},f::ScalarData,cache::BasicILMCache)
regularize_normal!(v::Edges{Primal},f::ScalarData,sys::ILMSystem)
```

操作 $\mathbf{v} = R_f \mathbf{n}\circ f$ は、スカラー表面データ `f`（スカラー電位のジャンプのようなもの）をグリッドデータ `v`（速度のようなもの）にマッピングします。これは [`normal_interpolate!`](@ref) の随伴です。
