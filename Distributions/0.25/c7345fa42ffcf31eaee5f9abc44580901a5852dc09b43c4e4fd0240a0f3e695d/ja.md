```
vec(d::Distribution{<:ArrayLikeVariate})
```

`d`の分布を持つ確率変数`X`の`vec(X)`の[`MultivariateDistribution`](@ref)を返します。

デフォルトの実装は[`ReshapedDistribution`](@ref)を返します。ただし、特定のタイプの分布や次元数に対してより最適化された分布を返すことができます。したがって、`ReshapedDistribution`のコンストラクタの代わりに`vec`を使用することをお勧めします。

# 実装

`vec(d)`は`reshape(d, length(d))`として定義されているため、`vec`ではなく`reshape(d, ::Tuple{Int})`を実装する必要があります。

参照: [`reshape`](@ref) ```
