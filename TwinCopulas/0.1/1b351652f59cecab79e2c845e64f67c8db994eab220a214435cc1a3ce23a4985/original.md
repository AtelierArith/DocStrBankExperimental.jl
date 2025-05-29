```
B11Copula{P}
```

Fields:

```
- θ::Real - parameter
```

Constructor

```
B11Copula(θ)
```

The bivariate B11 copula is parameterized by $\theta \in [0,1]$. It is constructed as: 

$$
C(u_1, u_2) = \theta \min\{u_1,u_2\} + (1-\theta)u_1u_2
$$

It has a few special cases: 

  * When θ = 0, it is the IndependentCopula
  * When θ = 1, is is the MCopula (Upper Frechet-Hoeffding bound)

References:

  * [Joe1997](@cite) Joe, Harry, Multivariate Models and Multivariate Dependence Concepts, Chapman & Hall. 1997.
