```
FrankCopula{P}
```

Fields:

  * θ::Real - parameter

Constructor

```
FrankCopula(θ)
```

The bivariate [Frank](https://en.wikipedia.org/wiki/Copula_(probability_theory)#Most_important_Archimedean_copulas) copula is parameterized by $\theta \in (-\infty,\infty)$. It is an Archimedean copula with generator : 

$$
\phi(t) = -\frac{\log\left(1+e^{-t}(e^{-\theta-1})\right)}{	heta}
$$

It has a few special cases: 

  * When θ = -∞, it is the WCopula (Lower Frechet-Hoeffding bound)
  * When θ = 1, it is the IndependentCopula
  * When θ = ∞, is is the MCopula (Upper Frechet-Hoeffding bound)

References:

  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
