```
id([T::Type=Float64,] V::TensorSpace) -> TensorMap
id!(t::AbstractTensorMap) -> AbstractTensorMap
```

空間 `V` 上の恒等エンドモルフィズムを構築します。すなわち、`domain(t) == codomain(t) == V` である `t::TensorMap` を返します。ここで、`T` が `Number` 型の場合は `scalartype(t) = T` となり、`T` が `DenseVector` 型の場合は `storagetype(t) = T` となります。

[`one!`](@ref) も参照してください。
