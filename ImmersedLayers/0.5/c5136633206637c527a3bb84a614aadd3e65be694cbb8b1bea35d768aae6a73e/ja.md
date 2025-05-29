```
normal_cross_interpolate!(vs::VectorData,s::Nodes{Dual},cache::BasicILMCache)
normal_cross_interpolate!(vs::VectorData,s::Nodes{Dual},sys::ILMSystem)
```

操作 $\mathbf{v}_s = \mathbf{n}\times R_N^T \psi\mathbf{e}_z)$ は、グリッドデータ `s`（流れ関数のような）をベクトル表面データ `vs`（表面の速度のような）にマッピングします。これはベクトル型キャッシュにのみ機能します。これは [`regularize_normal_cross!`](@ref) の負の随伴です。
