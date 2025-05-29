```
LogitNormal(μ,σ)
```

The *logit normal distribution* is the distribution of of a random variable whose logit has a [`Normal`](@ref) distribution. Or inversely, when applying the logistic function to a Normal random variable then the resulting random variable follows a logit normal distribution.

If $X \sim \operatorname{Normal}(\mu, \sigma)$ then $\operatorname{logistic}(X) \sim \operatorname{LogitNormal}(\mu,\sigma)$.

The probability density function is

$$
f(x; \mu, \sigma) = \frac{1}{x \sqrt{2 \pi \sigma^2}}
\exp \left( - \frac{(\text{logit}(x) - \mu)^2}{2 \sigma^2} \right),
\quad x > 0
$$

where the logit-Function is

$$
\text{logit}(x) = \ln\left(\frac{x}{1-x}\right)
\quad 0 < x < 1
$$

```julia
LogitNormal()        # Logit-normal distribution with zero logit-mean and unit scale
LogitNormal(μ)       # Logit-normal distribution with logit-mean μ and unit scale
LogitNormal(μ, σ)    # Logit-normal distribution with logit-mean μ and scale σ

params(d)            # Get the parameters, i.e. (μ, σ)
median(d)            # Get the median, i.e. logistic(μ)
```

The following properties have no analytical solution but numerical approximations. In order to avoid package dependencies for numerical optimization, they are currently not implemented.

```julia
mean(d)
var(d)
std(d)
mode(d)
```

Similarly, skewness, kurtosis, and entropy are not implemented.

External links

  * [Logit normal distribution on Wikipedia](https://en.wikipedia.org/wiki/Logit-normal_distribution)
