```
GumbelBarnettCopula{P}
```

Fields:

  * θ::Real - parameter

Constructor

```
GumbelBarnettCopula(θ)
```

The bivariate Gumbel-Barnett copula is parameterized by $\theta \in (0,1]$. It is an Archimedean copula with generator :

$$
\phi(t) = \exp{θ^{-1}(1-e^{t})}, 0 \leq \theta \leq 1.
$$

It has a few special cases: 

  * When θ = 0, it is the IndependentCopula

References:

  * [joe2014](@cite) Joe, H. (2014). Dependence modeling with copulas. CRC press, Page.437
  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
