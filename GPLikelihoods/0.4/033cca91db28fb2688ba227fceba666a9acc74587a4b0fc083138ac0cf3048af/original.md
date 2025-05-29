```
HeteroscedasticGaussianLikelihood(l=exp)
```

Heteroscedastic Gaussian likelihood.  This is a Gaussian likelihood whose mean and variance are functions of latent processes.

$$
    p(y|[f, g]) = \operatorname{Normal}(y | f, sqrt(l(g)))
$$

On calling, this would return a normal distribution with mean `f` and variance `l(g)`. Where `l` is link going from R to R^+
