```
BetaBinomial(n,α,β)
```

A *Beta-binomial distribution* is the compound distribution of the [`Binomial`](@ref) distribution where the probability of success `p` is distributed according to the [`Beta`](@ref). It has three parameters: `n`, the number of trials and two shape parameters `α`, `β`

$$
P(X = k) = {n \choose k} B(k + \alpha, n - k + \beta) / B(\alpha, \beta),  \quad \text{ for } k = 0,1,2, \ldots, n.
$$

```julia
BetaBinomial(n, α, β)      # BetaBinomial distribution with n trials and shape parameters α, β

params(d)       # Get the parameters, i.e. (n, α, β)
ntrials(d)      # Get the number of trials, i.e. n
```

External links:

  * [Beta-binomial distribution on Wikipedia](https://en.wikipedia.org/wiki/Beta-binomial_distribution)
