```
convolve(d1::Distribution, d2::Distribution)
```

Convolve two distributions and return the distribution corresponding to the sum of independent random variables drawn from the underlying distributions.

Currently, the function is only defined in cases where the convolution has a closed form. More precisely, the function is defined if the distributions of `d1` and `d2` are the same and one of

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

External links: [List of convolutions of probability distributions on Wikipedia](https://en.wikipedia.org/wiki/List_of_convolutions_of_probability_distributions)
