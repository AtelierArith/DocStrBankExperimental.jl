```
is_point(𝔤::LieAlgebra, X; kwargs...)
```

`X`がリー代数`𝔤`の有効な点であるかどうかを確認します。これは、`X`が`𝔤`の[`AbstractLieGroup`](@ref)の[`base_manifold`](@ref)`(G)`の[`identity_element`](@ref)`(G)`での接空間の有効な点であるかどうかを確認することに戻ります。
