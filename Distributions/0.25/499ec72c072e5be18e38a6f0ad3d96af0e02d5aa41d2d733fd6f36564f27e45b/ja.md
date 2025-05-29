```
Dirac(x)
```

*ディラック分布*は、その唯一の値`x`によってパラメータ化され、確率1でその値を取ります。

$$
P(X = \hat{x}) = \begin{cases}
1 & \quad \text{for } \hat{x} = x, \\
0 & \quad \text{for } \hat{x} \neq x.
\end{cases}
$$

```julia
Dirac(2.5)   # Dirac distribution with value x = 2.5
```

外部リンク:

  * [Dirac measure on Wikipedia](http://en.wikipedia.org/wiki/Dirac_measure)
