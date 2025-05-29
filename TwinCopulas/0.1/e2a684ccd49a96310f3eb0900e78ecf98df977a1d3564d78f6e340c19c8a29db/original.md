```
ClaytonCopula{P}
```

Fields:

  * θ::Real - parameter

Constructor

```
ClaytonCopula(d,θ)
```

The bivariate [Clayton](https://en.wikipedia.org/wiki/Copula_(probability_theory)#Most_important_Archimedean_copulas) copula is parameterized by $\theta \in [-1,\infty)$. It is an Archimedean copula with generator : 

$$
\phi(t) = \left(1+\mathrm{sign}(\theta)*t\right)^{-1\frac{1}{\theta}}
$$

It has a few special cases: 

  * When θ = -1, it is the WCopula (Lower Frechet-Hoeffding bound)
  * When θ = 0, it is the IndependentCopula
  * When θ = 1, it is the UtilCopula
  * When θ = ∞, is is the MCopula (Upper Frechet-Hoeffding bound)

References:

  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
