```
tEVCopula{P}
```

Fields:     - ν::Real - paremeter     - θ::Real - Parameter 

Constructor

```
tEVCopula(ν, θ)
```

The bivariate extreme t copula is parameterized by $\nu \in [0,\infty)$ and \theta \in (-1,1]. It is an Extreme value copula with Pickands dependence function: 

$$
A(x) = xt_{\nu+1}(Z_x) +(1-x)t_{\nu+1}(Z_{1-x})
$$

Where $t_{\nu + 1}$is the cumulative distribution function (CDF) of the standard t distribution with \nu + 1 degrees of freedom and

$$
Z_x = \frac{(1+\nu)^{1/2}{\sqrt{1-\theta^2}}\left [ \left (\frac{x}{1-x}  \right )^{1/\nu} - \theta \right ]
$$

It has a few special cases:

  * When θ = 0, it is the Independent Copula
  * When θ = ∞, it is the M Copula (Upper Frechet-Hoeffding bound)

References:

  * [Nikolopoulos2008](@cite) Extreme value properties of multivariate t copulas. Springer. 2008.
