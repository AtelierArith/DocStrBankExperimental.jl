```
surface_divergence_symm!(v::Edges{Primal},dv::VectorData,cache::BasicILMCache)
surface_divergence_symm!(v::Edges{Primal},dv::VectorData,sys::ILMSystem)
```

操作 $\mathbf{v} = D_s d\mathbf{v} = D R_t (\mathbf{n} \circ d\mathbf{v} + d\mathbf{v} \circ \mathbf{n})$ は、表面ベクトルデータ `dv`（速度のジャンプのような）をグリッドデータ `v`（速度のような）にマッピングします。これは [`surface_grad_symm!`](@ref) の負随伴です。微分操作は、`sys` が `IndexScaling` または `GridScaling` で指定されているかどうかに応じて、1 またはグリッドセルサイズで割られることに注意してください。
