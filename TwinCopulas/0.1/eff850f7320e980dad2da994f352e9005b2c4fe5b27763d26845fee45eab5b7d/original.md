```
Nelsen2Copula{P}
```

Fields:

  * θ::Real - parameter

Constructor

```
Nelsen2Copula(θ)
```

The bivariate Nelsen2Copula copula is parameterized by $\theta \in [1,\infty)$. It is an Archimedean copula with generator : 

$$
\phi(t) = 1 - t^{\frac{1}{\theta}}
$$

It has a few special cases: 

  * When θ = 1, it is the IndependentCopula
  * When θ = ∞, is is the MCopula (Upper Frechet-Hoeffding bound)

References:

  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
