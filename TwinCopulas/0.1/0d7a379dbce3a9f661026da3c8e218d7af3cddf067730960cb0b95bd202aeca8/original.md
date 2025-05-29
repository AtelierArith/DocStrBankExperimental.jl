```
AsymLogCopula{P}
```

Fields:

  * α::Real - Dependency parameter
  * θ::Vector - Asymmetry parameters (size 2)

Constructor

```
AsymLogCopula(α, θ)
```

The Asymmetric bivariate Logistic copula is parameterized by one dependence parameter $\alpha \in [1, \infty]$ and two asymmetry parameters $\theta_{i} \in [0,1], i=1,2$. It is an Extreme value copula with Pickands dependence function: 

$$
A(t) = (\theta_1^{\alpha}(1-t)^{\alpha} + \theta_2^{\alpha}t^{\alpha})^{\frac{1}{\alpha}} + (\theta_1 - \theta_2)t + 1 - \theta_1
$$

References:

  * [Tawn1988](@cite) Bivariate extreme value theory: models and estimation. Biometrika, 1988.
