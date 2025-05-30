```
surface_grad_cross!(γ::ScalarData,ϕ::Nodes{Primal},cache::BasicILMCache)
surface_grad_cross!(γ::ScalarData,ϕ::Nodes{Primal},sys::ILMSystem)
```

操作 $\gamma = \hat{G}_s\phi = \mathbf{e}_z \cdot (\mathbf{n} \times R_f^T G\phi)$ は、グリッドデータ `ϕ`（スカラー電位のような）をスカラー表面データ `γ`（表面渦度のような）にマッピングします。これは [`surface_divergence_cross!`](@ref) の随伴です。微分操作は、`sys` が `IndexScaling` または `GridScaling` で指定されているかどうかに応じて、1 またはグリッドセルサイズで割られることに注意してください。
