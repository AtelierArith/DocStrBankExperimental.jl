```
isometry([T::Type=Float64,] codomain::TensorSpace, domain::TensorSpace) -> TensorMap
isometry([T::Type=Float64,] codomain ← domain) -> TensorMap
isometry([T::Type=Float64,] domain → codomain) -> TensorMap
isometry!(t::AbstractTensorMap) -> AbstractTensorMap
```

コドメインとドメインの間の特定の等距離写像を構築します。すなわち、`scalartype(t) = T` が `T` が `Number` 型である場合、または `storagetype(t) = T` が `T` が `DenseVector` 型である場合に `t::TensorMap` を返します。等距離写像 `t` は `t' * t = id(domain)` および `(t * t')^2 = t * t'` を満たします。もし空間がそのような等距離包含を許可しない場合、エラーが発生します。

[`isomorphism`](@ref) および [`unitary`](@ref) も参照してください。
