```
LinearLogGamma(α, β, weights)
```

An unnormalized multivariate distribution derived from the LogGamma distribution. (see LogGamma)

The LinearLogGamma distribution is an distribution on a multidimensional `x`, derived from the LogGamma distribution. It is defined as:

$$
    LLG(x | lpha, eta, w) = LG(x^T w | a, b),
$$

where weights is a fixed vector of covariates, and lpha and eta are the scale and shape parameters of the LogGamma distribution, respectively. Fields

α::T: The scale parameter of the LogGamma distribution.

β::T: The shape parameter of the LogGamma distribution.

weights::C: The fixed vector of covariates.
