```
zero_vector(𝔤::LieAlgebra)
zero_vector(𝔤::LieAlgebra, T::Type)
zero_vector!(𝔤::LieAlgebra, X::T)
```

[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`) を生成します。これは、[`AbstractLieGroup`](@ref) `G` の [`LieAlgebra`](@ref) $𝔤$ の型 `T` のゼロベクトルです。デフォルトでは、これは `identity_element(G,T)` での `G` の多様体に対して `zero_vector` を呼び出します。

割り当てを行うバリアントでは、ゼロベクトルの型 `T` を指定できます。
