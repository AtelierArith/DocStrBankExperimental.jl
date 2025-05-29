```
BetaPrime(α, β)
```

The *Beta prime distribution* has probability density function

$$
f(x; \alpha, \beta) = \frac{1}{B(\alpha, \beta)}
x^{\alpha - 1} (1 + x)^{- (\alpha + \beta)}, \quad x > 0
$$

The Beta prime distribution is related to the [`Beta`](@ref) distribution via the relationship that if $X \sim \operatorname{Beta}(\alpha, \beta)$ then $\frac{X}{1 - X} \sim \operatorname{BetaPrime}(\alpha, \beta)$

```julia
BetaPrime()        # equivalent to BetaPrime(1, 1)
BetaPrime(α)       # equivalent to BetaPrime(α, α)
BetaPrime(α, β)    # Beta prime distribution with shape parameters α and β

params(d)          # Get the parameters, i.e. (α, β)
```

External links

  * [Beta prime distribution on Wikipedia](http://en.wikipedia.org/wiki/Beta_prime_distribution)
