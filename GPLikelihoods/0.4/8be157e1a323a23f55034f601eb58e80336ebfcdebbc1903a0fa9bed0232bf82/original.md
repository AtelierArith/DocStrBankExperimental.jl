```
NBParamFailure(failures)
```

Negative Binomial parametrization with `failures` the number of failures and `invlink(f)` the probability of success. This corresponds to the definition used by [Wikipedia](https://en.wikipedia.org/wiki/Negative_binomial_distribution).

$$
  p(y|\text{failures}, p=\text{invlink}(f)) = \frac{\Gamma(y+\text{failures})}{y! \Gamma(\text{failures})} p^y (1 - p)^{\text{failures}}
$$
