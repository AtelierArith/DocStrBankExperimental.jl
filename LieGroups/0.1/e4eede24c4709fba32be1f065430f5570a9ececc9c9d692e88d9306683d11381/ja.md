```
get_vector(G::AbstractLieGroup, c, B::AbstractBasis; kwargs...)
get_vector(𝔤::LieAlgebra, c, B::AbstractBasis; kwargs...)
get_vector!(G::AbstractLieGroup, X::T, c, B::AbstractBasis; kwargs...)
get_vector!(𝔤::LieAlgebra, X::T, c, B::AbstractBasis; kwargs...)
```

与えられた係数のセットに対応するベクトルを[`AbstractBasis`](@extref `ManifoldsBase.AbstractBasis`)の[`LieAlgebra`](@ref) `𝔤`で返します。すべての接ベクトルはリー代数で表されると仮定されるため、両方のシグネチャは同等です。この操作は、型`::T`の接ベクトル`X`のインプレースで実行できます。

デフォルトでは、この関数は[`identity_element`](@ref)`(G)`を必要とし、リー群が構築されているリーマン多様体の対応する[`get_vector`](@extref ManifoldsBase :jl:function:`ManifoldsBase.get_vectors`)関数を呼び出します。

逆の操作は[`get_coordinates`](@ref)です。

# キーワード引数

  * `tangent_vector_type` アロケーションバリアントに使用する接ベクトルの型を指定します。

他にも[`hat`](@ref)を参照してください。
