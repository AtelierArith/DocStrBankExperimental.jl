```
DefaultLieAlgebraOrthogonalBasis{𝔽} <: ManifoldsBase.AbstractOrthogonalBasis{𝔽,ManifoldsBase.TangentSpaceType}
```

リー代数の直交基底を指定します。これは、[`hat`](@ref) および [`vee`](@ref) 内でデフォルトとして使用されます。

リー群に対して特に上書き/実装されていない場合、[`identity_element`](@ref) の [`DefaultOrthogonalBasis`](@extref `ManifoldsBase.DefaultOrthogonalBasis`) が [`base_manifold](@ref base_manifold(::AbstractLieGroup)) でフォールバックとして機能します。

!!! note
    対応する [`get_coordinates`](@ref) および [`get_vector`](@ref) 関数を実装するには、`get_coordinates_lie(::AbstractLieAlgebra, X, B)` および `get_vector_lie(::AbstractLieAlgebra, X, B)` をそれぞれ定義してください。

