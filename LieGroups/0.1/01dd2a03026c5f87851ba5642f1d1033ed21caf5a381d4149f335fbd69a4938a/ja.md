```
exp(G::LieGroup{𝔽,<:AbelianMultiplicationGroupOperation}, X)
exp(G::LieGroup{𝔽,<:AbelianMultiplicationGroupOperation}, g, X)
exp!(G::LieGroup{𝔽,<:AbelianMultiplicationGroupOperation}, h, X)
exp!(G::LieGroup{𝔽,<:AbelianMultiplicationGroupOperation}, h, g, X)
```

[`LieGroup`](@ref) の点 `g` または [`Identity`](@ref) で [`AbelianMultiplicationGroupOperation`](@ref) を用いてリー群指数を計算します。

一部のアーベルリー群の表現の違いにより、このメソッドは `AbstractArray{<:Any,0}` 型の入力を持つ特定のアーベルリー群の具体的な実装をラップし、インプレース計算をサポートします。

`h` が `mutable` であれば、`h` のインプレース計算が可能です。
