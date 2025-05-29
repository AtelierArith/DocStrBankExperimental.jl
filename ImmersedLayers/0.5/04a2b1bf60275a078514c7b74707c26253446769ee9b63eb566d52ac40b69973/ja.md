```
surface_divergence!(Θ::Nodes{Primal},f::ScalarData,cache::BasicILMCache)
surface_divergence!(Θ::Nodes{Primal},f::ScalarData,sys::ILMSystem)
```

操作 $\theta = D_s f = D R_f \mathbf{n} \circ f$ は、表面スカラーデータ `f`（スカラー電位のジャンプのような）をグリッドデータ `Θ`（膨張、すなわち速度の発散のような）にマッピングします。これは [`surface_grad!`](@ref) の負随伴です。微分操作は、`sys` が `IndexScaling` または `GridScaling` で指定されているかどうかに応じて、1 またはグリッドセルサイズで割られることに注意してください。
