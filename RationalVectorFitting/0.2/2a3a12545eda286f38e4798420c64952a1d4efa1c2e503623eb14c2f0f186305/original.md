```
rational(s, poles, residues, d, h) -> `f(s)`
```

Rational transfer function with complex frequencies `s`, a set of poles `a_n`, residues `r_n` and real constants `d` and `h`.

$$
\sum_{n=1}^N \frac{r_n}{s - a_n} + d + s h
$$
