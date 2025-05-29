```
GaussianLikelihood(σ²)
```

Gaussian likelihood with `σ²` variance. This is to be used if we assume that the uncertainity associated with the data follows a Gaussian distribution.

$$
    p(y|f) = \operatorname{Normal}(y | f, σ²)
$$

On calling, this would return a normal distribution with mean `f` and variance σ².
