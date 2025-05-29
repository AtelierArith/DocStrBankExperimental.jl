```
regularize_normal_dot!(f::Nodes{Primal},vs::VectorData,cache::BasicILMCache)
regularize_normal_dot!(f::Nodes{Primal},vs::VectorData,sys::ILMSystem)
```

操作 $\phi = R_c \mathbf{n}\cdot \mathbf{v}_s$ は、表面ベクトルデータ `vs`（速度のジャンプのような）をグリッドノードデータ `f`（スカラー電位のような）にマッピングします。これは [`normal_dot_interpolate!`](@ref) の負の随伴です。
