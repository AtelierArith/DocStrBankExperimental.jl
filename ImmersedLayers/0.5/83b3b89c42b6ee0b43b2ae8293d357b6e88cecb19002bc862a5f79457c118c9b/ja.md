```
normal_cross_interpolate!(wn::ScalarData,v::Edges{Primal},cache::BasicILMCache)
normal_cross_interpolate!(wn::ScalarData,v::Edges{Primal},sys::ILMSystem)
```

操作 $w_n = e_z\cdot (\mathbf{n} \times R_f^T \mathbf{v})$ は、グリッドデータ `v`（速度のような）をスカラー表面データ `wn`（表面の渦度のような）にマッピングします。これは [`regularize_normal_cross!`](@ref) の負の随伴です。
