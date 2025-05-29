```
NoncentralChisq(ν, λ)
```

The *noncentral chi-squared distribution* with `ν` degrees of freedom and noncentrality parameter `λ` has the probability density function

$$
f(x; \nu, \lambda) = \frac{1}{2} e^{-(x + \lambda)/2} \left( \frac{x}{\lambda} \right)^{\nu/4-1/2} I_{\nu/2-1}(\sqrt{\lambda x}), \quad x > 0
$$

It is the distribution of the sum of squares of `ν` independent [`Normal`](@ref) variates with individual means $\mu_i$ and

$$
\lambda = \sum_{i=1}^\nu \mu_i^2
$$

```julia
NoncentralChisq(ν, λ)     # Noncentral chi-squared distribution with ν degrees of freedom and noncentrality parameter λ

params(d)    # Get the parameters, i.e. (ν, λ)
```

External links

  * [Noncentral chi-squared distribution on Wikipedia](https://en.wikipedia.org/wiki/Noncentral_chi-squared_distribution)
