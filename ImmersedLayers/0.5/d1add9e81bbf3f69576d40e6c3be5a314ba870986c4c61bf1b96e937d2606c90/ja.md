```
interpolate!(vb::VectorData,v::Edges{Primal},cache::BasicILMCache)
interpolate!(vb::VectorData,v::Edges{Primal},sys::ILMSystem)
```

操作 $\mathbf{v}_b = R_c^T \mathbf{v}$ は、ベクトルグリッドデータ `v` をスカラー点データ `vb` の形で表面点に補間します。これは [`regularize!`](@ref) の随伴です。
