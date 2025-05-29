```
mean_and_cov(f::FiniteGP)
```

Equivalent to `(mean(f), cov(f))`, but sometimes more efficient to compute them jointly than separately.

```jldoctest
julia> fx = GP(SqExponentialKernel())(range(-3.0, 3.0; length=10), 0.1);

julia> mean_and_cov(fx) == (mean(fx), cov(fx))
true
```
