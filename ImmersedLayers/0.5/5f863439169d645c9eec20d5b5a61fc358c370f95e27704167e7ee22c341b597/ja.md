```
regularize!(s::Nodes{Primal},f::ScalarData,cache::BasicILMCache)
regularize!(s::Nodes{Primal},f::ScalarData,sys::ILMSystem)
```

操作 $s = R_c f$ は、スカラー表面データ `f` をスカラーグリッドデータ `s` の形でグリッドに正則化します。これは [`interpolate!`](@ref) の随伴です。
