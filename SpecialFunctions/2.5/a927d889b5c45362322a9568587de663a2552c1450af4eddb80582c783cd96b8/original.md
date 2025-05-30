```
gamma_inc_inv_psmall(a, logr)
```

Compute `x0` - initial approximation when `p` is small. Here we invert the series in Eqn (2.20) in the paper and write the inversion problem as:

$$
x = r\left[1 + a\sum_{k=1}^{\infty}\frac{(-x)^{n}}{(a+n)n!}\right]^{-1/a},
$$

where $r = (p\Gamma(1+a))^{1/a}$ Inverting this relation we obtain $x = r + \sum_{k=2}^{\infty} c_{k} r^{k}$.
