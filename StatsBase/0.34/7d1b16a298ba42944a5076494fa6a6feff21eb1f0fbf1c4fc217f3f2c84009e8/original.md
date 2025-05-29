```
genmean(a, p)
```

Return the generalized/power mean with exponent `p` of a real-valued array, i.e. $\left( \frac{1}{n} \sum_{i=1}^n a_i^p \right)^{\frac{1}{p}}$, where `n = length(a)`. It is taken to be the geometric mean when `p == 0`.
