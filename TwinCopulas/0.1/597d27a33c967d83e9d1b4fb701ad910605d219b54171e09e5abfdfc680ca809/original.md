```
GaussianCopula{P}
```

Fields:

  * θ::Real - Parameter

Constructor

```
GaussianCopula(θ)
```

The bivariate [Gaussian](https://en.wikipedia.org/wiki/Copula_(probability_theory)#Gaussian_copula) copula. It is constructed as: 

$$
C(u_1, u_2; \theta) = \Phi_{\theta}(\Phi^{-1}(u_1),\Phi^{-1}(u_2))
$$

where $\Phi_{\theta}$ is the cumulative distribution function (CDF) of a standard bivariate normal distribution with correlation coefficient $\theta \in  [-1, 1]$ and $\Phi^{-1}$is the quantile function of the standard normal distribution.

It has a few special cases:

  * When θ = -1, it is the WCopula (Lower Frechet-Hoeffding bound)
  * When θ = 0, it is the IndependentCopula
  * When θ = 1, is is the MCopula (Upper Frechet-Hoeffding bound)

References:

  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
