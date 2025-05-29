```
MEWMC(λ, value)
```

An Exponentially Weighted Moving Covariance Matrix statistic with smoothing constant `λ` and initial value `value`.

The update mechanism for $C_t$ based on a new observation `x \in \mathbb{R}^p` is given by

$Z_t = (1 - λ)Z_{t-1} + λ \cdot xx'$,

and the chart value is defined as

$C_t = \text{tr}(Z_t) - \log|Z_t| - p$.

### References

Hawkins, D. M., & Maboudou-Tchao, E. M. (2008). Multivariate Exponentially Weighted Moving Covariance Matrix. Technometrics, 50(2), 155-166.
