```
BC2Copula{P}
```

Fields:

```
- θ1::Real - parameter
- θ1::Real - parameter
```

Constructor

```
BC2Copula(θ1, θ2)
```

The bivariate BC₂ copula is parameterized by two parameters $\theta_{i} \in [0,1], i=1,2$. It is an Extreme value copula with Pickands dependence function: 

$$
A(t) = \max\{\theta_1 t, \theta_2(1-t) \} + \max\{(1-\theta_1)t, (1-\theta_2)(1-t)\}
$$

References:

  * [Mai2011](@cite) Bivariate extreme-value copulas with discrete Pickands dependence measure. Springer, 2011.
