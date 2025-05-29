```
univariate_maximize(f, a::Real, b::Real, transform, optimizer::BrentsMethodOpt, t::Real; ε::Real=sqrt(eps))
```

Brentの方法を使用して`f(x)`を最大化します。`?brents_method_minimize`を参照してください。
