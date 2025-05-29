```
ksmin(x, hardness=50)
```

Kreisselmeier–Steinhauser constraint aggregation function.  In the limit as `hardness` goes to infinity the minimum function is returned. Is mathematically guaranteed to underestimate the minimum function, i.e. `minimum(x) <= ksmin(x, hardness)`.
