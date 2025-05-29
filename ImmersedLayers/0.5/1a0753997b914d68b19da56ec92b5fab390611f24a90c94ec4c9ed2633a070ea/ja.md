```
normal_dot_interpolate!(vs::VectorData,f::Nodes{Primal},cache::BasicILMCache)
normal_dot_interpolate!(vs::VectorData,f::Nodes{Primal},sys::ILMSystem)
```

操作 $\mathbf{v}_s = \mathbf{n} R_c^T \phi$ は、グリッドノードデータ `f`（スカラー電位のような）をサーフェスベクターデータ `vs`（速度のような）にマッピングします。これは [`regularize_normal_dot!`](@ref) の負の随伴です。
