```
interpolate!(f::ScalarData,s::Nodes{Dual},cache::BasicILMCache)
interpolate!(f::ScalarData,s::Nodes{Dual},sys::ILMSystem)
```

操作 $f = R_N^T s$ は、スカラーグリッド（カール）データ `s` をスカラー点データ `f` の形で表面点に補間します。ベクターデータのためにキャッシュが構築されている場合にのみ機能します。これは [`regularize!`](@ref) の随伴です。
