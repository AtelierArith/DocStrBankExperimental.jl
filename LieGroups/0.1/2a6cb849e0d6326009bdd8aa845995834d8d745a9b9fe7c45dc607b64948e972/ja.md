```
get_coordinates(𝔤::LieAlgebra, X::T, B::AbstractBasis)
get_coordinates!(𝔤::LieAlgebra, c, X::T, B::AbstractBasis)
```

`X`の[`AbstractBasis`](@extref `ManifoldsBase.AbstractBasis`)に関する分解の座標ベクトルを[`LieAlgebra`](@ref) `𝔤`に対して返します。この操作は`c`のインプレースで実行できます。

デフォルトでは、この関数は[`identity_element`](@ref)`(G, T)`が利用可能であることを要求し、リー群が構築されているリーマン多様体の対応する[`get_coordinates`](@extref ManifoldsBase :jl:function:`ManifoldsBase.get_coordinates`)関数を呼び出します。

逆の操作は[`get_vector`](@ref)です。

また、[`vee`](@ref)も参照してください。
