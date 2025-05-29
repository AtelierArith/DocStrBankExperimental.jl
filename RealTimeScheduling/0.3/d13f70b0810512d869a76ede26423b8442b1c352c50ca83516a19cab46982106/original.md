```
request_bound(τ::AbstractRealTimeTask, t)
```

Compute the request bound function (RBF) for the task `τ`.

$$
\left\lceil \frac{t}{\mathrm{period}(τ)}\right\rceil \mathrm{cost}(τ)
$$
