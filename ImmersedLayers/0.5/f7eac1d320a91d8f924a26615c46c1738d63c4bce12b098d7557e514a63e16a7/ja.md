```
surface_divergence_cross!(Θ::Nodes{Primal},f::ScalarData,cache::BasicILMCache)
surface_divergence_cross!(Θ::Nodes{Primal},f::ScalarData,sys::ILMSystem)
```

操作 $\theta = \hat{D}_s f = D R_f \mathbf{n} \times f \mathbf{e}_z$ は、表面スカラーデータ `f`（流れ関数のジャンプのような）をグリッドデータ `Θ`（膨張、すなわち速度の発散のような）にマッピングします。これは [`surface_grad_cross!`](@ref) の随伴です。微分操作は、`sys` が `IndexScaling` または `GridScaling` で指定されているかどうかに応じて、1またはグリッドセルサイズで割られることに注意してください。
