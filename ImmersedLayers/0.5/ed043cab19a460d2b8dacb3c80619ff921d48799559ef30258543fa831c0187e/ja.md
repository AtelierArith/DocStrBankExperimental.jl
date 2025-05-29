```
w_cross_v!(vw::Edges{Primal},w::Nodes{Dual},v::Edges{Primal},base_cache::BasicILMCache,extra_cache::RotConvectiveDerivativeCache)
```

渦度 `w` と速度 `v` の項 `w \times v` を計算し、結果を `vw` に返します。このメソッドのバージョンは、[`RotConvectiveDerivativeCache`](@ref) 型の `extra_cache` を使用します。
