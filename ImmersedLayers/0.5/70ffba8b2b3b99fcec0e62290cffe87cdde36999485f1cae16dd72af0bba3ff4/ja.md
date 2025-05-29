```
surface_grad!(vn::ScalarData,ϕ::Nodes{Primal},cache::BasicILMCache)
surface_grad!(vn::ScalarData,ϕ::Nodes{Primal},sys::ILMSystem)
```

操作 $v_n = G_s\phi = \mathbf{n} \cdot R_f^T G\phi$ は、グリッドデータ `ϕ`（スカラー電位のような）をスカラー表面データ `vn`（速度の法線成分のような）にマッピングします。これは [`surface_divergence!`](@ref) の負随伴です。微分操作は、`sys` が `IndexScaling` または `GridScaling` で指定されているかどうかに応じて、1 またはグリッドセルサイズで割られることに注意してください。
