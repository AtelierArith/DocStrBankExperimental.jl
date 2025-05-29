```
gkldiv(a, b)
```

Compute the generalized Kullback-Leibler divergence between two arrays: $\sum_{i=1}^n (a_i \log(a_i/b_i) - a_i + b_i)$. Efficient equivalent of `sum(a*log(a/b)-a+b)`.
