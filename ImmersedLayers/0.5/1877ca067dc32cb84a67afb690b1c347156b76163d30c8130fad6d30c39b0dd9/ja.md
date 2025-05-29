```
normal_interpolate!(vn::ScalarData,v::Edges{Primal},cache::BasicILMCache)
normal_interpolate!(vn::ScalarData,v::Edges{Primal},sys::ILMSystem)
```

操作 $v_n = \mathbf{n} \cdot R_f^T \mathbf{v}$ は、グリッドデータ `v`（速度のような）をスカラー表面データ `vn`（表面速度の法線成分のような）にマッピングします。これは [`regularize_normal!`](@ref) の随伴です。
