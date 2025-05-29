```
SurvivalCopula{P}
```

Fields:

```
- C::bicopula
```

Constructor

```
SurvivalCopula(C)
```

The bivariate Survival copula is defined as

$$
\overbar{C}(u_1,u_2) = C(u_1, u_2) + u_1 + u_2 - 1
$$

Where $C(u_1, u_2)$ is a copula as we know them.

References:

  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
