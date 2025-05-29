```
UtilCopula{}
```

Constructor

```
UtilCopula()
```

The bivariate UtilCopula is a simple copula that appears as a special case of several copulas, that has the form :  

$$
C(u_1, u_2) = \frac{u_1u_2}{u_1+u_2 - u_1u_2}
$$

It happends to be an Archimedean Copula, with generator : 

$$
\phi(t) = 1 / (t + 1)
$$

References:

  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
