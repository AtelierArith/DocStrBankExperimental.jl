```
AsymMixedCopula{P}
```

Fields:

  * θ::Vector - parameters (size 2)

Constructor

```
AsymMixedCopula(θ)
```

The Asymmetric bivariate Mixed copula is parameterized by two parameters $\theta_{i}, i=1,2$ that must meet the following conditions:

  * θ₁ ≥ 0
  * θ₁+θ₂ ≤ 1
  * θ₁+2θ₂ ≤ 1
  * θ₁+3θ₂ ≥ 0

It is an Extreme value copula with Pickands dependence function: 

$$
A(t) = \theta_{2}t^3 + \theta_{1}t^2-(\theta_1+\theta_2)t+1
$$

It has a few special cases:

  * When θ₁ = θ₂ = 0, it is the Independent Copula
  * When θ₂ = 0, it is the Mixed Copula

References:

  * [Tawn1988](@cite) Bivariate extreme value theory: models and estimation. Biometrika, 1988.
