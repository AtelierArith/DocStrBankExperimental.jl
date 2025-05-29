```
MEWMS(λ, value)
```

Exponentially weighted moving covariance matrix with smoothing constant `λ`.

The update mechanism based on a new observation `x \in \mathbb{R}^p` is given by

$Z_t = (1 - λ)\cdot Z_{t-1} + λ \cdot xx'$,

and the chart value is defined as

$C_t = \textrm{tr}(Z_t).$

### References

Huwang, L., Yeh, A. B., & Wu, C.-W. (2007). Monitoring Multivariate Process Variability for Individual Observations. Journal of Quality Technology, 39(3), 258-278. https://doi.org/10.1080/00224065.2007.11917692
