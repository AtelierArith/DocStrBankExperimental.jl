```
convective_derivative!(vdp::Nodes{Primal},v::Edges,p::Nodes{Primal},base_cache::BasicILMCache,extra_cache::ConvectiveDerivativeCache)
```

`p`の対流微分を速度`v`を用いて計算します。すなわち、$v\cdot \nabla p$を計算し、その結果を`vdp`に返します。結果は、`base_cache`が`IndexScaling`型か`GridScaling`型かに応じて、1またはグリッドセルサイズで割られます。このメソッドのバージョンは、[`ConvectiveDerivativeCache`](@ref)型の`extra_cache`を使用します。
