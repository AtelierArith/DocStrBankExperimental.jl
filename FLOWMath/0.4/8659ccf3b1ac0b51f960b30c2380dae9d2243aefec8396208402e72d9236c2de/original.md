```
ksmax(x, hardness=50)
```

Kreisselmeier–Steinhauser constraint aggregation function.  In the limit as `hardness` goes to infinity the maximum function is returned. Is mathematically guaranteed to overestimate the maximum function, i.e. `maximum(x) <= ksmax(x, hardness)`.
