```
ar1_whitenoise(x::AbstractVector)
```

Return the AR1 regression coefficient of a time series `x` by computing the analytic solution of the least-square parameter estimation under white-noise assumption for the data-generating process:

$$
\theta = \sum_{i=2}^{n} x_i  x_{i-1} / \sum_{i=2}^{n} x_{i-1}^2
$$
