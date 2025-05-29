```
AMHCopula{P}
```

Fields:

  * θ::Real - parameter

Constructor

```
AMHCopula(θ)
```

The bivariate [AMH](https://en.wikipedia.org/wiki/Copula_(probability_theory)#Most_important_Archimedean_copulas) copula is parameterized by $\theta \in [-1,1)$. It is an Archimedean copula with generator : 

$$
\phi(t) = 1 - \frac{1-\theta}{e^{-t}-\theta}
$$

It has a few special cases: 

  * When θ = 0, it is the IndependentCopula
  * When θ = 1, it is the UtilCopula

References:

  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
