```
ll, e = update!(f::AbstractFilter, u, y, p = parameters(f), t = index(f))
```

Perform one step of `predict!` and `correct!`, returns log-likelihood and prediction error
