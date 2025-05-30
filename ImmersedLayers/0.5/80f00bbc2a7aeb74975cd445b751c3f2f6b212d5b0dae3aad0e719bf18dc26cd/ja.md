```
regularize!(s::Nodes{Dual},f::ScalarData,cache::BasicILMCache)
regularize!(s::Nodes{Dual},f::ScalarData,sys::ILMSystem)
```

操作 $s = R_N f$ は、スカラー表面データ `f` をスカラーグリッド（カール）データ `s` の形式でグリッドに正則化します。ベクターデータのためにキャッシュが構築されている場合にのみ機能します。これは [`interpolate!`](@ref) の随伴です。
