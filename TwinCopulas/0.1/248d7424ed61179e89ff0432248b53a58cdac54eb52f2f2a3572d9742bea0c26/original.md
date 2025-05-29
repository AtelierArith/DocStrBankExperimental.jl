```
CuadrasAugeCopula{P}
```

Fields:

```
- α::Real - parameter
```

Constructor

```
CuadrasAugeCopula(α)
```

The bivariate Cuadras Auge copula is parameterized by $\alpha \in [0,1]$. It is an Extreme value copula with Pickands dependence function: 

$$
A(t) = \max\{t, 1-t \} + (1-\theta)\max\{t, 1-t\}
$$

References:

  * [Mai2017](@cite) Simulating copulas: stochastic models, sampling algorithms, and applications. 2017.
