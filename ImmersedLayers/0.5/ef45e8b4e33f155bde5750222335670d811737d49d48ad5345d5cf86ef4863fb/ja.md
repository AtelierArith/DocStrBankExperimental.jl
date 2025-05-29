```
interpolate!(f::ScalarData,s::Nodes{Primal},cache::BasicILMCache)
interpolate!(f::ScalarData,s::Nodes{Primal},sys::ILMSystem)
```

操作 $f = R_c^T s$ は、スカラーグリッドデータ `s` をスカラー点データ `f` の形で表面点に補間します。これは [`regularize!`](@ref) の随伴です。
