```
RafteryCopula{P}
```

Fields:

```
- θ::Real - parameter
```

Constructor

```
RafteryCopula(θ)
```

The bivariate Raftery Copula is parameterized by $\theta \in [0,1]$. It is constructed as: 

$$
C(u_1, u_2) = \min\{u_1,u_2\} +\frac{1-\theta}{1+\theta}(u_1u_2)^{1/(1-\theta)}\left \{1-(\max\{u_1,u_2\})^{-(1+\theta)/(1-\theta)}  \right \}
$$

It has a few special cases: 

  * When θ = 0, it is the Independent Copula
  * When θ = 1, it is the MCopula (Upper Frechet-Hoeffding bound)

References:

  * [Joe1997](@cite) Joe, Harry, Multivariate Models and Multivariate Dependence Concepts, Chapman & Hall. 1997.
