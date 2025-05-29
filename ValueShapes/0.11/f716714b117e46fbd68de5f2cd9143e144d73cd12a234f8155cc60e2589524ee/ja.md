```
ReshapedDist <: Distribution
```

与えられた [`AbstractValueShape`](@ref) を使用して再形成された多変量分布。

コンストラクタ:

```julia
    ReshapedDist(dist::MultivariateDistribution, shape::AbstractValueShape)
```

さらに、`MultivariateDistribution`s は次のように再形成できます。

```julia
(shape::AbstractValueShape)(dist::MultivariateDistribution)
```

違いは次の通りです。

```julia
(shape::ArrayShape{T,1})(dist::MultivariateDistribution)
```

は `ReshapedDist` の代わりに元の `dist` を返します。
