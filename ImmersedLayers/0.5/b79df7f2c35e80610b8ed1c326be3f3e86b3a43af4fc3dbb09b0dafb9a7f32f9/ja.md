```
regularize_normal_dot!(v::Edges{Primal},taus::TensorData,cache::BasicILMCache)
regularize_normal_dot!(v::Edges{Primal},taus::TensorData,sys::ILMSystem)
```

操作 $\mathbf{v} = R_f \mathbf{n}\cdot \mathbf{\tau}_s$ は、表面テンソルデータ `taus`（応力のような）をグリッドエッジデータ `v`（速度のような）にマッピングします。これは [`normal_dot_interpolate!`](@ref) の負の随伴です。
