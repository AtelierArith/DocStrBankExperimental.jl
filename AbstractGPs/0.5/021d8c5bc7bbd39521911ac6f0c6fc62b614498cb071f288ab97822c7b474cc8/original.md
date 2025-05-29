```
cov(fx::FiniteGP, gx::FiniteGP)
```

Compute the cross-covariance matrix between `fx` and `gx`.

```jldoctest
julia> f = GP(Matern32Kernel());

julia> x1 = randn(11);

julia> x2 = randn(13);

julia> cov(f(x1), f(x2)) == kernelmatrix(Matern32Kernel(), x1, x2)
true
```
