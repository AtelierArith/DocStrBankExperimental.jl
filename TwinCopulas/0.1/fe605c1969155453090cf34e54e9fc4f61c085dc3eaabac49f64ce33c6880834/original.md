```
GalambosCopula{P}
```

Fields:

```
- θ::Real - parameter
```

Constructor

```
GalambosCopula(θ)
```

The bivariate Galambos copula is parameterized by $\alpha \in [0,\infty)$. It is an Extreme value copula with Pickands dependence function: 

$$
A(t) = 1 - (t^{-\theta}+(1-t)^{-\theta})^{-\frac{1}{\theta}}
$$

It has a few special cases:

  * When θ = 0, it is the Independent Copula
  * When θ = ∞, it is the M Copula (Upper Frechet-Hoeffding bound)

References:

  * [Galambos1975](@cite) Order statistics of samples from multivariate distributions. J. Amer. Statist Assoc. 1975.
