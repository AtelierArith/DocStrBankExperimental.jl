```
inv(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, g)
inv!(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, h, g)
```

群の逆元 $g^{-1}$ を計算します。これは [`AbelianMultiplicationGroupOperation`](@ref) に対してスカラー入力の場合、通常のスカラー逆元 $g^{-1}$ に簡略化されます。

いくつかのアーベルリー群の表現の違いにより、このメソッドは `AbstractArray{<:Any,0}` 型の入力を持つ特定のアーベル LieGroup の具体的な実装をラップし、インプレース計算をサポートします。

`h` が `mutable` であれば、`h` のインプレースで計算できます。
