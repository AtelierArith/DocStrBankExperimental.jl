```
log(G::LieGroup{𝔽,<:AbelianMultiplicationGroupOperation}, h)
log(G::LieGroup{𝔽,<:AbelianMultiplicationGroupOperation}, g, h)
log!(G::LieGroup{𝔽,<:AbeliantMultiplicationGroupOperation}, X, g)
log!(G::LieGroup{𝔽,<:AbeliantMultiplicationGroupOperation}, X, g, h)
```

具体的な[`AbelianMultiplicationGroupOperation`](@ref)のインスタンスを用いて、点`g`または[`Identity`](@ref)での[`LieGroup`](@ref)の対数を計算します。

いくつかのアーベルLie群の表現の違いにより、このメソッドは、`AbstractArray{<:Any,0}`型の入力を持つ特定のアーベルLieGroupの具体的な実装をラップし、インプレース計算をサポートします。

`X`が`mutable`であれば、`X`のインプレースで計算できます。
