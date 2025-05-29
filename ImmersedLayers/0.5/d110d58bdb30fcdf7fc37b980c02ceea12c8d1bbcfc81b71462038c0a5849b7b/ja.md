```
convective_derivative!(vdw::Nodes{Dual},v::Edges,w::Nodes{Dual},base_cache::BasicILMCache,extra_cache::ConvectiveDerivativeCache)
```

`w`の対流微分を速度`v`を用いて計算します。すなわち、$v\cdot \nabla w$を計算し、その結果を`vdw`に返します。結果は、`base_cache`が`IndexScaling`型か`GridScaling`型かに応じて、1またはグリッドセルサイズで割られます。このバージョンのメソッドは、[`ConvectiveDerivativeCache`](@ref)型の`extra_cache`を使用します。
