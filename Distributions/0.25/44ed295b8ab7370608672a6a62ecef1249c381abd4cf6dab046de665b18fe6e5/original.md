```
SkewedExponentialPower(μ, σ, p, α)
```

The *Skewed exponential power distribution*, with location `μ`, scale `σ`, shape `p`, and skewness `α`, has the probability density function [1]

$$
f(x; \mu, \sigma, p, \alpha) =
\begin{cases}
\frac{1}{\sigma 2p^{1/p}\Gamma(1+1/p)} \exp \left\{ - \frac{1}{2p}\Big| \frac{x-\mu}{\alpha \sigma} \Big|^p \right\}, & \text{if } x \leq \mu \\
\frac{1}{\sigma 2p^{1/p}\Gamma(1+1/p)} \exp \left\{ - \frac{1}{2p}\Big| \frac{x-\mu}{(1-\alpha) \sigma} \Big|^p \right\}, & \text{if } x > \mu
\end{cases}.
$$

The Skewed exponential power distribution (SEPD) incorporates the Laplace ($p=1, \alpha=0.5$), normal ($p=2, \alpha=0.5$), uniform ($p\rightarrow \infty, \alpha=0.5$), asymmetric Laplace ($p=1$), skew normal ($p=2$), and exponential power distribution ($\alpha = 0.5$) as special cases.

[1] Zhy, D. and V. Zinde-Walsh (2009). Properties and estimation of asymmetric exponential power distribution. *Journal of econometrics*, 148(1):86-96, 2009.

```julia
SkewedExponentialPower()            # SEPD with shape 2, scale 1, location 0, and skewness 0.5 (the standard normal distribution)
SkewedExponentialPower(μ, σ, p, α)  # SEPD with location μ, scale σ, shape p, and skewness α
SkewedExponentialPower(μ, σ, p)     # SEPD with location μ, scale σ, shape p, and skewness 0.5 (the exponential power distribution)
SkewedExponentialPower(μ, σ)        # SEPD with location μ, scale σ, shape 2, and skewness 0.5 (the normal distribution)
SkewedExponentialPower(μ)           # SEPD with location μ, scale 1, shape 2, and skewness 0.5 (the normal distribution)

params(d)       # Get the parameters, i.e. (μ, σ, p, α)
shape(d)        # Get the shape parameter, i.e. p
location(d)     # Get the location parameter, i.e. μ
scale(d)        # Get the scale parameter, i.e. σ
```
