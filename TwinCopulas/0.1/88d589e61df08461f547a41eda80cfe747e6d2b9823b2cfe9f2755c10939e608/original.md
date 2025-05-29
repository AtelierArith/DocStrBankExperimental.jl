```
MardiaCopula{P}
```

Fields:

```
- θ::Real - parameter
```

Constructor

```
MardiaCopula(θ)
```

The bivariate Mardia copula is parameterized by $\theta \in [-1,1]$. It is constructed as: 

$$
C(u_1, u_2) = \frac{\theta^2(1+\theta)}{2}\min\{u_1,u_2\} + (1-\theta^2)u_1u_2 + \frac{\theta^2(1-\theta)}{2}\max\{u_1+u_2-1,0\}
$$

It has a few special cases: 

  * When θ = 0, it is the Independent Copula
  * When θ = 1, it is the MCopula (Upper Frechet-Hoeffding bound)
  * When θ = -1, is is the WCopula (Lower Frechet-Hoeffding bound)

References:

  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
