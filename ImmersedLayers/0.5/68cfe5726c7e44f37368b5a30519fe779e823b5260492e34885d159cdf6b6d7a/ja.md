```
surface_grad_symm!(τ::VectorData,v::Edges{Primal},cache::BasicILMCache)
surface_grad_symm!(τ::VectorData,v::Edges{Primal},sys::ILMSystem)
```

操作 $\mathbf{\tau} = G_s v = \mathbf{n} \cdot R_t^T (G \mathbf{v} + (G \mathbf{v})^T)$ は、グリッドベクトルデータ `v`（速度のような）をベクトル表面データ `τ`（牽引のような）にマッピングします。これは [`surface_divergence_symm!`](@ref) の負随伴です。微分操作は、`sys` が `IndexScaling` または `GridScaling` で指定されているかどうかに応じて、1 またはグリッドセルサイズで割られます。
