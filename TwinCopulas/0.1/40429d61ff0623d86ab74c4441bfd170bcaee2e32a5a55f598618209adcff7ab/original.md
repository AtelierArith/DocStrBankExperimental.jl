```
MaresiasCopula{P}
```

Fields:

```
- G::Function
```

Constructor

```
MaresiasCopula(G)
```

The bivariate Maresias copula is parameterized by functions $G, H: [0,1] \to [0,1]$, such that $G(u) = 2u - H(u), u \in [0,1]$. It is constructed as: 

$$
C(u_1, u_2) = \frac{1}{2}\left ( G(u_1)G(u_2) + H(u_1)H(u_2) \right )
$$

References:

  * [Mai2017](@cite) Simulating copulas: stochastic models, sampling algorithms, and applications. 2017.
