```
equalMixCovarianceKnown_moments(k, sample)
```

Use the given parameters to compute the sample moments necessary for parameter estimation with equal mixing coefficients and shared known covariances.

Returns moments 0 to `k` for the first dimension, and moments m*{je*1+e_i} for j in 0 to `k`-1 and i in 2 to d as a matrix where d is the dimension, i varies across rows, and j varies down columns.
