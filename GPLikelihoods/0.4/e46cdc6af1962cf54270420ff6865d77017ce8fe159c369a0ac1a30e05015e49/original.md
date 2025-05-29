```
NBParamSuccess(successes)
```

Negative Binomial parametrization with `successes` the number of successes and `invlink(f)` the probability of success. This corresponds to the definition used by [Distributions.jl](https://juliastats.org/Distributions.jl/latest/univariate/#Distributions.NegativeBinomial).

$$
  p(y|\text{successes}, p=\text{invlink}(f)) = \frac{\Gamma(y+\text{successes})}{y! \Gamma(\text{successes})} p^\text{successes} (1 - p)^y
$$
