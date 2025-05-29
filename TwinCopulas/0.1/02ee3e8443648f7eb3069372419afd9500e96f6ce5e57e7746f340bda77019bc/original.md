```
MixedCopula{P}
```

Fields:

```
- θ::Real - parameter
```

Constructor

```
MixedCopula(θ)
```

The bivariate Mixed copula is parameterized by $\alpha \in [0,1]$. It is an Extreme value copula with Pickands dependence function: 

$$
A(t) = \theta t^2 - \theta t + 1
$$

It has a few special cases: 

  * When θ = 0, it is the IndependentCopula

References:

  * [Tawn1988](@cite) Bivariate extreme value theory: models and estimation. Biometrika, 1988.
