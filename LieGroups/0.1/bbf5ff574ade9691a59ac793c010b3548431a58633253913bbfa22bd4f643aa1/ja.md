```
lie_bracket!(𝔤::LieAlgebra{𝔽,AdditionGroupOperation}, X, Y)
lie_bracket!(𝔤::LieAlgebra{𝔽,AdditionGroupOperation}, Z, X, Y)
```

リー括弧 $[⋅,⋅]: \mathfrak g×\mathfrak g → \mathfrak g$ を計算します。これは [`AdditionGroupOperation`](@ref) の場合、対応する [`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`) に簡略化されます。この計算は `Z` のインプレースで行うことができます。
