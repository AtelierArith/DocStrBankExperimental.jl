```
PositivePoisson(λ)
```

A *PositivePoisson distribution* (aka zero-truncated Poisson, ZTP) descibes the number of independent events occurring within a unit time interval, given the average rate of occurrence `λ` and, importantly, given that the number is not zero.

$P(X = k) = \frac{λ^k}{k!(1-e^{-λ})} e^{-λ}, \quad \text{ for } k = 1,2,\ldots.$

```julia
PositivePoisson()        # PositivePoisson distribution with rate parameter 1
PositivePoisson(lambda)       # PositivePoisson distribution with rate parameter lambda

params(d)        # Get the parameters, i.e. (λ,)
mean(d)          # Get the mean arrival rate, i.e. λ
```

External links:

  * [PositivePoisson distribution on Wikipedia](https://en.wikipedia.org/wiki/Zero-truncated_Poisson_distribution)
