```
tCopula{P}
```

Fields:     - ν::Real - paremeter     - θ::Real - Parameter 

Constructor

```
tCopula(ν, θ)
```

The bivariate t copula. It is constructed as: 

$$
C(u_1, u_2; \nu, \theta) = t_{\nu, \theta}(t_{\nu}^{-1}(u_1),t_{\nu}^{-1}(u_2))
$$

where $t_{\nu, \theta}$ is the cumulative distribution function (CDF) of a bivariate t-distribution with $\nu \in \mathbb{R}^{+}$ degrees of freedom, zero means, and correlation $\theta \in [-1, 1]$, and $t_{\nu}^{-1}$ is the quantile function of the standard t-distribution with $\nu$ degrees of freedom.

It has a few special cases:

  * When θ = -1, it is the WCopula (Lower Frechet-Hoeffding bound)
  * When θ = 0, it is the IndependentCopula
  * When θ = 1, is is the MCopula (Upper Frechet-Hoeffding bound)

References:

  * [joe2014](@cite) Joe, Harry. Dependence modeling with Copulas. Chapman & Hall, 2014.
