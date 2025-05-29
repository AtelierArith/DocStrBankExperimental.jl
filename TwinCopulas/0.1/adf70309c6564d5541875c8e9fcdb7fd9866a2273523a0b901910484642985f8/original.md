```
GumbelCopula{P}
```

Fields:

  * θ::Real - parameter

Constructor

```
GumbelCopula(d,θ)
```

The bivariate [Gumbel](https://en.wikipedia.org/wiki/Copula_(probability_theory)#Most_important_Archimedean_copulas) copula is parameterized by $\theta \in [1,\infty)$. It is an Archimedean copula with generator : 

$$
\phi(t) = \exp{-t^{\frac{1}{θ}}}
$$

It has a few special cases: 

  * When θ = 1, it is the IndependentCopula
  * When θ = ∞, is is the MCopula (Upper Frechet-Hoeffding bound)

References:

  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
