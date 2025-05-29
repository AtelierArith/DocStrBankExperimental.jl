```
log(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, g)
log!(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, X, g)
```

具体的な[`AbstractMultiplicationGroupOperation`](@ref)のインスタンスを持つ[`LieGroup`](@ref)上でリー群の対数を計算します。これは[(行列)の対数](https://en.wikipedia.org/wiki/Logarithm_of_a_matrix)に簡略化されます。

これは`X`のインプレースで計算できます。
