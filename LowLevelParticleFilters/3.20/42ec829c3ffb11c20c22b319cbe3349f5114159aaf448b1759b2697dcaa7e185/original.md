```
ll = logsumexp!(w, we [, maxw])
```

Normalizes the weight vector `w` and returns the weighted log-likelihood

https://arxiv.org/pdf/1412.8695.pdf eq 3.8 for p(y) https://discourse.julialang.org/t/fast-logsumexp/22827/7?u=baggepinnen for stable logsumexp
