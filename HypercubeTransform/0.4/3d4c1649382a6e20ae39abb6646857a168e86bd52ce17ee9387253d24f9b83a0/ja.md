```
`ascube(c)
```

単位ハイパーキューブから分布空間に移動するために必要な情報を含むオブジェクトを構築します。これは変換を構築する際に使用する通常の関数です。

オブジェクトのタイプに応じて、いくつかの異なる動作があります。

  * `c::Distribution` の場合、これは分布を保存します。
  * `c::Tuple{AbstractHypercubeTransform}` の場合、これはタプルを保存します。

# 例

```julia
ascube(Normal())
ascube(MultivariateNormal())
ascube((Normal(), Normal(2.0)))
ascube( (α = Uniform(), β = Normal()) )
```
