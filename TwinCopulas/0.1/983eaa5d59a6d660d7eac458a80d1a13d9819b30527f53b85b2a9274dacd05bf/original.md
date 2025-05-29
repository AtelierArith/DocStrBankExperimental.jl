```
EmpiricalCopula{M}
```

Fields:

```
-data::M - 2xn matrix observations
```

Constructor

```
EmpiricalCopula(data)
```

Let $(x_k, y_k), k = 1,2, \ldots, n$ denote a sample of size $n$ from continuous bivariate distribution. The Empirical Copula is the function

$$
C_n(\frac{i}{n},\frac{j}{n}) = \frac{\text{number of pairs (x,y) in the sample with} x \leq x_{(i)}, y \leq y_{(j)}}{n}
$$

For more details see

References:

  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
