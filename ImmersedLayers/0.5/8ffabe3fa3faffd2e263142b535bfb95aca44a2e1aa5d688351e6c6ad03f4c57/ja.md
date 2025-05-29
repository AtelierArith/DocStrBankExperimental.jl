```
regularize!(v::Edges{Primal},vb::VectorData,cache::BasicILMCache)
regularize!(v::Edges{Primal},vb::VectorData,sys::ILMSystem)
```

操作 $\mathbf{v} = R_f \mathbf{v}_b$ は、ベクトル表面データ `vb` をスカラーグリッドデータ `v` の形でグリッドに正則化します。これは [`interpolate!`](@ref) の随伴です。
