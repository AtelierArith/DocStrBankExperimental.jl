```
HuslerReissCopula{P}
```

Fields:

```
- θ::Real - parameter
```

Constructor

```
HuslerReissCopula(θ)
```

The bivariate Husler-Reiss copula is parameterized by $\theta \in [0,\infty)$. It is an Extreme value copula with Pickands dependence function: 

$$
A(t) = t\Phi(\theta^{-1}+\frac{1}{2}\theta\log(\frac{t}{1-t})) +(1-t)\Phi(\theta^{-1}+\frac{1}{2}\theta\log(\frac{1-t}{t}))
$$

Where $\Phi$is the cumulative distribution function (CDF) of the standard normal distribution.

It has a few special cases:

  * When θ = 0, it is the Independent Copula
  * When θ = ∞, it is the M Copula (Upper Frechet-Hoeffding bound)

References:

  * [Husler1989](@cite) Maxima of normal random vectors: between independence and complete dependence. Statist. Probab. 1989.
