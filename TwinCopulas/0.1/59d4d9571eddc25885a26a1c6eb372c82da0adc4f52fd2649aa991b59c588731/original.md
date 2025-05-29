```
MorgensternCopula{P}
```

Fields:

```
- θ::Real - parameter
```

Constructor

```
MorgensternCopula(θ)
```

The bivariate Morgenstern copula or FGM Copula is parameterized by $\theta \in [-1,1]$. It is constructed as: 

$$
C(u_1, u_2) = u_1u_2(1+\theta(1-u_1)(1-u_2))
$$

It has a few special cases: 

  * When θ = 0, it is the Independent Copula

References:

  * [Joe1997](@cite) Joe, Harry, Multivariate Models and Multivariate Dependence Concepts, Chapman & Hall. 1997.
