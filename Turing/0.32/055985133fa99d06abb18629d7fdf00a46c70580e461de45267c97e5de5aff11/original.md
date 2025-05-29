```
BinomialLogit(n, logitp)
```

The *Binomial distribution* with logit parameterization characterizes the number of successes in a sequence of independent trials.

It has two parameters: `n`, the number of trials, and `logitp`, the logit of the probability of success in an individual trial, with the distribution

$$
P(X = k) = {n \choose k}{(\text{logistic}(logitp))}^k (1 - \text{logistic}(logitp))^{n-k}, \quad \text{ for } k = 0,1,2, \ldots, n.
$$

See also: [`Binomial`](@ref)
