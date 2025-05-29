```
LogCopula{P}
```

Fields:

```
- θ::Real - parameter
```

Constructor

```
LogCopula(θ)
```

The bivariate Logistic copula (or Gumbel Copula) is parameterized by $\theta \in [1,\infty)$. It is an Extreme value copula with Pickands dependence function: 

$$
A(t) = (t^{\theta}+(1-t)^{\theta})^{\frac{1}{\theta}}
$$

It has a few special cases: 

  * When θ = 1, it is the IndependentCopula
  * When θ = ∞, is is the MCopula (Upper Frechet-Hoeffding bound)

References:

  * [Tawn1988](@cite) Bivariate extreme value theory: models and estimation. Biometrika, 1988.
