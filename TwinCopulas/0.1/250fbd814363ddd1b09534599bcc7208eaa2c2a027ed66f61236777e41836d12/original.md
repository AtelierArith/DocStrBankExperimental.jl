```
FrechetCopula{P}
```

Fields:

```
- θ1::Real - parameter
- θ2::Real - parameter
```

Constructor

```
FrechetCopula(θ1, θ2)
```

The bivariate Fréchet copula is parameterized by $\theta_{i} \in [0,1], i = 1,2$, such that $\theta_1 + \theta_2 \leq 1 \$. It is constructed as: 

$$
C(u_1, u_2) = \theta_1 \min\{u_1, u_2\} + (1- \theta_1 - \theta_2)u_1u_2 + \theta_2 \max\{u_1 + u_2 - 1, 0\}
$$

It has a few special cases: 

  * When θ1 = θ2 = 0, it is the Independent Copula
  * When θ1 = 1, it is the MCopula (Upper Frechet-Hoeffding bound)
  * When θ2 = 1, is is the WCopula (Lower Frechet-Hoeffding bound)

References:

  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
