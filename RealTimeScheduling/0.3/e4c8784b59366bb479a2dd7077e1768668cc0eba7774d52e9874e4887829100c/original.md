```
demand_bound(τ::AbstractRealTimeTask, t)
```

Compute Baruah's demand bound function (DBF) for the task `τ`.

$$
\max\left(0, \left\lfloor \frac{t - \mathrm{deadline}(τ)}{\mathrm{period}(τ)} + 1 \right\rfloor \mathrm{cost}(τ) \right)
$$
