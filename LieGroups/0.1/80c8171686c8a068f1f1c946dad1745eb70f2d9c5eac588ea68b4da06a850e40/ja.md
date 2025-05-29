```
exp(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, X)
exp!(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, g, X)
```

[`LieGroup`](@ref) と [`AbstractMultiplicationGroupOperation`](@ref) を持つリー群の指数を計算します。これは [行列指数](https://en.wikipedia.org/wiki/Matrix_exponential) に簡略化されます。

これは `g` のインプレースで計算できます。
