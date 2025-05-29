```
normal_dot_interpolate!(taus::TensorData,v::Edges{Primal},cache::BasicILMCache)
normal_dot_interpolate!(taus::TensorData,v::Edges{Primal},sys::ILMSystem)
```

操作 $\mathbf{\tau}_s = \mathbf{n}\circ R_f^T\mathbf{v}$ は、グリッドエッジデータ `v`（速度のような）をサーフェステンソルデータ `taus`（応力のような）にマッピングします。これは [`regularize_normal_dot!`](@ref) の負随伴です。
