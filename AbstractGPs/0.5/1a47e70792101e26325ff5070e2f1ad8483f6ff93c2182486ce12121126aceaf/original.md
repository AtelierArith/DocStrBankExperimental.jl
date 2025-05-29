```
posterior(fx::FiniteGP, y::AbstractVector{<:Real})
```

Construct the posterior distribution over `fx.f` given observations `y` at `fx.x` made under noise `fx.Σy`. This is another `AbstractGP` object. See chapter 2 of [1] for a recap on exact inference in GPs. This posterior process has mean function

```julia
m_posterior(x) = m(x) + k(x, fx.x) inv(cov(fx)) (y - mean(fx))
```

and kernel

```julia
k_posterior(x, z) = k(x, z) - k(x, fx.x) inv(cov(fx)) k(fx.x, z)
```

where `m` and `k` are the mean function and kernel of `fx.f`, respectively.
