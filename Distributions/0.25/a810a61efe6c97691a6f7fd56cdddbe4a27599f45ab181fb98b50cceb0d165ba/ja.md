```
convolve(d1::Distribution, d2::Distribution)
```

2つの分布を畳み込み、基となる分布から引き出された独立な確率変数の和に対応する分布を返します。

現在、この関数は畳み込みに閉じた形がある場合にのみ定義されています。より正確には、`d1` と `d2` の分布が同じであり、次のいずれかである場合に関数が定義されます。

  * [`Bernoulli`](@ref)
  * [`Binomial`](@ref)
  * [`NegativeBinomial`](@ref)
  * [`Geometric`](@ref)
  * [`Poisson`](@ref)
  * [`DiscreteNonParametric`](@ref)
  * [`Normal`](@ref)
  * [`Cauchy`](@ref)
  * [`Chisq`](@ref)
  * [`Exponential`](@ref)
  * [`Gamma`](@ref)
  * [`MvNormal`](@ref)

外部リンク: [List of convolutions of probability distributions on Wikipedia](https://en.wikipedia.org/wiki/List_of_convolutions_of_probability_distributions)
