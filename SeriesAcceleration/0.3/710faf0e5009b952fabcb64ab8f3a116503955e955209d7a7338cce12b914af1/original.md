```
rateOfConv(arr:AbstractArray{T, 1})
```

Estimates rate of convergence $\alpha_n = \frac{\log |(x_{n+1} - x_n)/(x_n - x_{n-1})|}{\log |(x_n - x_{n-1})/(x_{n-1}-x_{n-2})|}$ from array. `trace` can be set to true, to obtain the roc for all partial sums.
