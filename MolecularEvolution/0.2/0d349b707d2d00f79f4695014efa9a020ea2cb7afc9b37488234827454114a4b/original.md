```
univariate_maximize(f, a::Real, b::Real, transform, optimizer::BrentsMethodOpt, t::Real; ε::Real=sqrt(eps))
```

Maximizes `f(x)` using Brent's method. See `?brents_method_minimize`.
