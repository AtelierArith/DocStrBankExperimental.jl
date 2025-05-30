```
regularize_normal_cross!(w::Nodes{Dual},vs::VectorData,cache::BasicILMCache)
regularize_normal_cross!(w::Nodes{Dual},vs::VectorData,sys::ILMSystem)
```

操作 $\omega = R_N \mathbf{n}\times \mathbf{v}_s$ は、表面ベクトルデータ `vs`（速度のジャンプのようなもの）をグリッドデュアルノードデータ `w`（渦度のようなもの）にマッピングします。これはベクトルデータキャッシュ専用です。これは [`normal_cross_interpolate!`](@ref) の負随伴です。
